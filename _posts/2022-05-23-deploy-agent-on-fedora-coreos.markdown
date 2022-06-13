---
layout: post
title: "Deploy flotta-agent on Fedora CoreOS 35"
date: 2022-05-23 12:00:00 +1000
categories: flotta 
author: Cosmin Tupangiu
tags:
  - guide
  - flotta
  - fcos
  - flotta-agent 

summary-1: Deploy flotta-agent on Fedora CoreOS 35
---

During development, the user may need to spin off a large number of Edge Devices. Fedora CoreOS provides an easy way to create
a virtual machine to deploy Edge Device on it. Moreover, the relatively low footprint of CoreOS VM allows you to have a large number of 
Edge Devices on the same host.

## General `flotta-agent` installation

`Flotta-agent` can be installed on any machine using the `rpm` provided by the [fedora copr](https://copr.fedorainfracloud.org/coprs/project-flotta/).
To install `flotta-agent`:
```bash
sudo dnf copr enable project-flotta/flotta 
sudo dnf install -y flotta-agent
```

Now, that `flotta-agent` has been installed on the OS, we need to configure `yggdrasil` to know how to connect to `Flotta Edge API`.
By default, the configuration file can be found under `/etc/yggdrasil/config.toml`.
An example of `yggdrasil` configuration file is provided below:
```yaml
log-level = "debug"
cert-file = "/etc/pki/consumer/cert.pem"
key-file = "/etc/pki/consumer/key.pem"
ca-root = ["/etc/pki/consumer/ca.pem"]
path-prefix = "api/flotta-management/v1"
protocol = "http"
client-id = "<some-id>"
server = "flotta.io:8043"
```

Let's explain line by line the configuration:

- `log-level`: sets the log level for `yggdrasil`. The options are: `debug`, `info`, `warn`, `error`.
- `cert-file`, `key-file`: path to client certification and private key.
- `ca-root`: CA root certification file.
- `path-prefix`: this is set to `api/flotta-management/v1`. All the request from the Edge Device will start with prefix followed by the id of the device (e.g. `/api/flotta-management/v1/data/<device-id>/in`).
- `protocol`: set to `http`. 
- `server`: address of the `Flotta Edge API`. The domain name has to be the same as the domain set in the cluster because the certificates are valid only for that domain. The domain can be set in the cluster by modifying the configmap `flotta-operator-manager-config` and set `DOMAIN` to you desired value.
- `client-id`: the id of the client. Generally, we set this id to `/etc/machine-id` but you can use any value as long it is unique. 

The certificates can be obtained by running `make get-certs` in `Flotta Operator` cluster.

## Creation of the ignition file

CoreOS configures the system using an [ignition](https://docs.fedoraproject.org/en-US/fedora-coreos/producing-ign/) file. The `ignition` file is produced from a `butane` file.
You can find the specification of the `butane` file on [coreos/butane](https://coreos.github.io/butane/config-fcos-v1_3/). Basically, the `butane` file is a `yaml` file which specify
how the system will be configured after startup. 

All the system configuration is done via `systemd` so to install and setup `flotta-agent` we need to create two services. These services run only one time when we are provisioning the system.

### Install `flotta-agent`

Installing the `flotta-agent` through `systemd` requires adding `flotta-agent copr` and run `rpm-ostree`.

**Remark**: CoreOS is an `ostree` OS hence it is using `rpm-ostree` instead of `dnf`.

The service could look like this:
```yaml
[Unit]
Description=Flotta setup service
Wants=network-online.target
After=network-online.target
ConditionPathExists=!/usr/lib/systemd/system/yggdrasild.service

[Service]
Type=oneshot
ExecStartPre=curl https://copr.fedorainfracloud.org/coprs/project-flotta/flotta/repo/fedora-35/project-flotta-flotta-fedora-35.repo -o /etc/yum.repos.d/project-flotta.repo
ExecStart=rpm-ostree install flotta-agent
ExecStart=/bin/bash -c "echo \"client-id = ##`cat /etc/machine-id`##\" >> /etc/yggdrasil/config.toml"
ExecStart=sed -i -s "s/##/\"/g" /etc/yggdrasil/config.toml
ExecStopPost=systemctl reboot

[Install]
WantedBy=multi-user.target
```

For those not familiar with `systemd`, here are some explications:

- The service must start after the `network-online.target` meaning we need to have an internet connection.
- `ConditionPathExists` must be true for this service to start. This condition allows us to start this service only if `yggdrasild.service` has not been install yet.
- Before actually install the `flotta-agent`, we need to setup the `copr`. This is done with the target `ExecStartPre`
- `ExecStart` installs what we need. The next `ExecStart` targets are set the `client-id`. Basically, what we what is to modify the provided `yggdrasil` configuration file to set the `client-id` to the `machine-id`. 
   This id is unique for each vm and it is available after the first run so we need to capture this id and added to `yggdrasil` configuration file.
- Finally, when everything is installed we reboot the vm with `ExecStopPost`


### Enabling `flotta-agent` services

Normally, after you install a new service you need to run `systemctl enable --now <service>`. In CoreOS, to do this, we need another `service`:
```
[Unit]
Description=Flotta start service
Wants=network-online.target
After=network-online.target
ConditionPathExists=/usr/lib/systemd/system/yggdrasild.service
ConditionPathExists=!/etc/systemd/system/multi-user.target.wants/yggdrasild.service

[Service]
Type=oneshot
ExecStart=systemctl enable --now yggdrasild.service
ExecStart=systemctl enable --now node_exporter.service

[Install]
WantedBy=multi-user.target
```

Here we have the same problem as before: we need to run this service only once at provisioning time. 
For that, we use two `ConditionPathExists`. The first one is checking if `yggdrasild.service` has been installed and the second is checking that `yggdrasild.service` hasn't been yet enabled.

### Butane file
Now, that we have the install and setup services, let's create our butane file step by step.

```yaml
variant: fcos
version: 1.3.0
passwd:
  users:
    - name: core
      uid: 1000
      ssh_authorized_keys:
        - ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAICsx5m3Pu9nxayhj6FIdNfzE2ppSlKqbJ9OJgG74jV9Q cosmin@fedora
```

First we add a user and a ssh key. SSH key can be generated with `ssh-key-gen`. Here we put our public key.

Next, we specify the `systemd` services:
```yaml
systemd:
  units:
    # Enable auto-login for 'core' user.
    - name: serial-getty@ttyS0.service
      dropins:
      - name: autologin-core.conf
        contents: |
          [Service]
          ExecStart=
          ExecStart=-/usr/sbin/agetty --autologin core --noclear %I $TERM
          TTYVTDisallocate=no
    - name: zincati.service
      mask: true
    - name: podman.service
      enabled: true
    - name: podman.socket
      enabled: true
    - name: nftables.service
      enabled: true
    - name: flotta-setup.service
      enabled: true
    - name: flotta-start.service
      enabled: true
```

`Flotta-agent` needs `podman` and `nftables` services to run. Also, we are adding our two custom services `flotta-setup` and `flotta-start` to install and setup flotta.
The first service is not mandatory but it is providing auto-login which is can be very useful. If you don't use `noautoconsole` option in `virt-install`, the service `auto-login` will automatically log the user when the boot finished.

The next section is the storage:
```yaml
storage:
  trees:
    - path: /etc/systemd/system
      local: systemd/
  directories:
    - path: /etc/pki/consumer
      mode: 0700
  files:
    # Hostname for virtual host.
    - path: /etc/hostname
      mode: 0644
      contents:
        inline: edgedevice
    # Certificates
    - path: /etc/pki/consumer/key.pem
      mode: 0666
      contents:
        local: files/key.pem
      user:
        id: 1000
    - path: /etc/pki/consumer/cert.pem
      mode: 0666
      contents:
        local: files/cert.pem
      user:
        id: 1000
    - path: /etc/pki/consumer/ca.pem
      mode: 0666
      contents:
        local: files/ca.pem
      user:
        id: 1000
    - path: /etc/yggdrasil/config.toml
      mode: 0666
      contents:
        local: files/config.toml
    # Dont log audit messages
    - path: /etc/sysctl.d/20-silence-audit.conf
      mode: 0644
      contents:
        inline: |
          # Raise console message logging level from DEBUG (7) to WARNING (4)
          # to hide audit messages from the interactive console.
          kernel.printk=4
    # Set operator hostname
    - path: /etc/hosts
      overwrite: true
      contents:
        inline: |
          IPADDRESS DOMAIN
    # linger root
    - path: /etc/systemd/logind.conf
      overwrite: true
      contents:
        inline: |
          KillExcludeUsers=root
    # disable selinux
    - path: /etc/selinux/config
      overwrite: true
      contents:
        inline: |
          SELINUX=disabled
          SELINUXTYPE=targeted
```

First, we need to copy our custom services to `systemd` folder. This is done under `trees` section.
The section `directories` creates the `/etc/pki/customer` folder where we will copy the certificates. Next, we copy the certificates and the configuration file from the host to vm.
The modification of `20-silence-audit.conf` is not mandatory but it will be useful not to have those debug messages in the log.

A couple more files and we are done. First we need to setup `Flotta API` address and domain in the `/etc/hosts` file. 
Next, we are enabling `linger` for `root` and disabling `SELINUX`.

Voilà! We are done with the `butane` file. 

All that is rest is arrange all these file like this:
```
.
├── files
│   ├── ca.pem
│   ├── cert.pem
│   ├── config.toml
│   └── key.pem
├── spec.bu
└── systemd
    ├── flotta-setup.service
    └── flotta-start.service

```

The folder `files` contains the files to be copied to OS and `system` folder contains our custom services.

### Generate ignition file

The ignition file can be generate either with `podman` or directly by installing `butane`:

##### Via podman

```bash
podman run --interactive --rm quay.io/coreos/butane:release \
       --pretty --strict spec.bu spec.ign
```

##### Via butane

Butane is available as Fedora package:
```bash
sudo dnf install -y butane
```

Run butane on the Butane file:
```bash
butane --pretty --strict spec.bu > spec.ign
```

### Ignite CoreOS instance

For this blog, I use `libvirt` but you have lots of other solutions to create your instance. Please take a look at CoreOS [doc](https://docs.fedoraproject.org/en-US/fedora-coreos/).

After we fetch the latest image for `qemu`, the instance can be lunched using:
```bash
IGNITION_CONFIG="spec.ign"
IMAGE="/path/to/image.qcow2"
VM_NAME="fcos-test-01"
VCPUS="2"
RAM_MB="2048"
STREAM="stable"
DISK_GB="10"

virt-install --connect="qemu:///system" --name="${VM_NAME}" --vcpus="${VCPUS}" --memory="${RAM_MB}" \
        --os-variant="fedora-coreos-$STREAM" --import --graphics=none \
        --disk="size=${DISK_GB},backing_store=${IMAGE}" \
        --network bridge=virbr0 \
        --qemu-commandline="-fw_cfg name=opt/com.coreos/config,file=${IGNITION_CONFIG}"

```

If you don't want to see the console, you can add `--noautoconsole` to virt-install command.

Everything that we did here, you can find it on [Github](https://github.com/tupyy/flotta-agent-coreos).
