---
layout: post
title: "Flotta Developer CLI"
date: 2022-07-20 12:00:00 +1000
categories: flotta
author: Ariel Ireni, Moti Asayag, Gloria Ciavarrini
tags:
- guide
- flotta
- dev-cli

summary-1: Getting started with Flotta Developer CLI
---

Flotta Developer CLI was created to enable easy creation of edge devices and deploy predefine workloads on them.
The CLI creates edge devices as docker containers, therefore docker is a requirement for the CLI to work.
The CLI uses the local k8s cluster pointed by the `$KUBECONFIG` environment variable or `$HOME/.kube/config` to obtain
necessary information for the registration process.

To get started using the developer CLI, install the Flotta Developer CLI.
Packages are available for fc36, epel8 and epel9 at project-flotta COPR repository.
```shell
sudo dnf -y copr enable project-flotta/flotta-testing
sudo dnf -y install flotta-dev-cli
```

You may enable auto-completion for the CLI by running the following command:
```shell
flotta completion bash > /usr/share/bash-completion/completions/flotta
```
Or (if the above command failed with permission denied error):
```shell
flotta completion bash | sudo tee /usr/share/bash-completion/completions/flotta
```

And by pressing the `TAB` key, you can use the auto-completion:
```shell
flotta <tab><tab><tab>
flotta
add         (Add a new flotta resource)                                   list        (List flotta resources)
completion  (Generate the autocompletion script for the specified shell)  start       (Start flotta resource)
delete      (Delete the flotta resource)                                  stop        (Stop flotta resource)
help        (Help about any command)
```

Now, you can easily add a new edge device by running:
```shell
$ flotta add device --name device1
device 'device1' was added 
```
Note that the first execution of this command will take some since the edge-device image is being pulled to the local
image registry. The image will be available for the next executions.

You can view edge device `device1` under the list of the registered devices:
```shell
$ flotta list device
NAME		STATUS		CREATED		
device1		running		46 seconds ago	
```

Once you have a registered edge device, you can deploy workloads on it:
```shell
$ flotta add workload --device device1
workload 'nginx1-21-6-ygneqhis' was added to device 'device1'
```

To view list of workloads use:
```shell
$ flotta list workload
NAME			STATUS		CREATED		
nginx1-21-6-ygneqhis	Running		2 minutes ago	
nginx1-21-6-kkejlmol	Running		5 minutes ago	
```

You can also stop and start a registered device:
```shell
$ flotta stop device --name device1
edgedevice 'device1' was stopped 

# view stopped device status
$ flotta list device
NAME		STATUS		CREATED		
device1		exited		2 minutes ago

# start device
$ flotta start device --name device1
device 'device1' was started 

# view started device status
$ flotta list device
NAME		STATUS		CREATED		
device1		running		3 minutes ago	
```

Finally, if you wish to delete a device or workload, you can run:
```shell
# delete workload
$ flotta delete workload --name nginx1-21-6-kkejlmol
workload 'nginx1-21-6-kkejlmol' was deleted 

# delete device
$ flotta delete device --name device1
device 'device1' was deleted 
```

## Troubleshooting
As things might not always be clear, here are some tips to help you:
* _flotta-dev-cli_ runs the edge device as a container, therefore you need to have docker installed and permissions to
  pull and image and to create a container.
* Workloads are deployed as containers(by _podman_) in the edge device (a nested container).
* Workloads are run under the _flotta_ user. Workloads debugging needs to be done also as _flotta_ user on the device.

### Debug the device
In order to register the device, the Flotta Edge API certificates need to be used to establish communication. To download the certificates run the following from flotta-operator project:
```shell
# remove old certs, if exists
$ sudo rm /tmp/*.pem
# download new certs, from the flotta operator project
$ make get-certs
# set permissions
$ sudo chown root:root /tmp/*.pem
```

To connect to a device, use docker command to list the running edge device containers and their status:
```shell
→ docker ps --filter label=flotta
CONTAINER ID   IMAGE                                      COMMAND         CREATED          STATUS         PORTS   NAMES
1ca4bf233b2f   quay.io/project-flotta/edgedevice:latest   "/sbin/init"    25 minutes ago   Up 25 minutes          edge1
```
With the device name or container ID, you can connect to the device by running:
```shell
→ docker exec -it edge1 bash
[root@1ca4bf233b2f project]#
```
Once connected to device, the _yggdrasil_ daemon can be checked for errors:
```shell
[root@1ca4bf233b2f project]# systemctl status yggdrasild
● yggdrasild.service - yggdrasil daemon
     Loaded: loaded (/usr/lib/systemd/system/yggdrasild.service; disabled; vendor preset: disabled)
     Active: active (running) since Tue 2022-07-26 12:58:04 UTC; 38min ago
       Docs: https://github.com/redhatinsights/yggdrasil
   Main PID: 128 (yggdrasild)
      Tasks: 30 (limit: 5671)
     Memory: 134.1M
        CPU: 12.229s
     CGroup: /system.slice/yggdrasild.service
             ├─ 128 /usr/sbin/yggdrasild
             └─ 147 /usr/libexec/yggdrasil/device-worker
```
And so _yggdrasil_ logs can be viewed as well. The log contains also the output of the device-worker which is flotta's
component that runs the workloads. The log can be viewed by running:
```shell
[root@1ca4bf233b2f project]# journalctl -u yggdrasild
```
View logs is useful when you are debugging a device, failure to register or failure to deploy workloads.

### Debug the workload
In case of failure to run the workload, the output of listing the workloads may show an undesired status:
```shell
→ flotta list workload
NAME                    STATUS  CREATED
nginx1-21-6-xmkdetkh    Exited  40 minutes ago
```

In order to debug a failure to run a workload, there is a need to connect as _flotta_ user.
_flotta_ user was created with _nologin_ shell, therefore you need to specify one to become _flotta_ user:
```shell
→ docker exec -it 1ca4bf233b2f /bin/bash
[root@1ca4bf233b2f project]# id
uid=0(root) gid=0(root) groups=0(root)

# expected to fail
[root@1ca4bf233b2f project]# su - flotta
This account is currently not available.

# expected to succeed
[root@1ca4bf233b2f project]# su - flotta -s /bin/sh
-sh-5.1$ id
uid=1001(flotta) gid=1001(flotta) groups=1001(flotta)
-sh-5.1$
```

As _flotta_ user, you can view the workload system files:
```shell
[flotta@1ca4bf233b2f ~]$ ls -l /var/home/flotta/.config/systemd/user/
total 16
-rw-r--r--. 1 root   root    936 Jul 26 13:00 container-nginx1-21-6-xmkdetkh-nginx1-21-6-xmkdetkh.service
drwxr-xr-x. 2 flotta flotta 4096 Jul 26 13:00 default.target.wants
-rw-r--r--. 1 root   root    858 Jul 26 13:00 nginx1-21-6-xmkdetkh.service
drwxr-xr-x. 2 flotta flotta 4096 Jul 26 12:58 sockets.target.wants
```
and test their status:
```shell
[flotta@1ca4bf233b2f ~]$ systemctl status nginx1-21-6-xmkdetkh.service
```

Examine podman service status:
```shell
[flotta@1ca4bf233b2f ~]$ systemctl --user status podman
● podman.service - Podman API Service
     Loaded: loaded (/usr/lib/systemd/user/podman.service; disabled; vendor preset: disabled)
     Active: active (running) since Wed 2022-07-27 12:05:58 UTC; 47min ago
TriggeredBy: ● podman.socket
       Docs: man:podman-system-service(1)
   Main PID: 203 (podman)
      Tasks: 13 (limit: 5671)
     Memory: 18.6M
        CPU: 10.142s
     CGroup: /user.slice/user-1001.slice/user@1001.service/app.slice/podman.service
             └─ 203 /usr/bin/podman --log-level=info system service
```
And view podman logs to find for issues to run the workload:
```shell
[flotta@366d67a90f10 ~]$ journalctl --user -u podman
```

If you find an issue with _flotta-dev-cli_, please report it to the [Github issue tracker](https://github.com/project-flotta/flotta-dev-cli/issues).

### Use your own flotta-worker-device image
If you need to use a different `flotta-worker-device` image than the official one (e.g. to test changes you made to the device-worker before sending a PR) then you must:

1. Create your custom `flotta-worker-device` image\
In the `flotta-device-worker` project folder execute:
```shell
IMG=quay.io/<YOUR_USERNAME>/flotta-device-worker:latest make deploy-container-image
```
This command creates the image and push it on your repository.
Make sure this repository is public.

1. Set the environment variable `DEVICE_IMAGE`\
   When running the `flotta` command set the environment variable `DEVICE_IMAGE` to use your previously created image:
   
   ```shell
   DEVICE_IMAGE=quay.io/<YOUR_USERNAME>/flotta-device-worker:latest flotta add device --name edge1
   ```