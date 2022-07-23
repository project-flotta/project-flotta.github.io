---
layout: documentation
---

# Accessing host devices from a workload

To reduce the security thread that can generate from running workloads at the edge, flotta is configured by default to run the workloads in rootless containers. While this increases the device's security and prevents pods from escaping containers and having full access to the device, it also impacts a few use cases where there is a need to access mounted host devices such as webcams, sensors or other plugged devices, since the containers are no longer able to access the mounted devices.

Even in a rootless container and with SELinux enabled, it is possible for workloads to have access to a mounted device, provided that the host and the workload are configured properly.


## Adding the supplementary group to the `flotta` user ##

To run the workloads in a rootless mode, the flotta agent creates the `flotta` user when installed. At the same time, the device agent leverages on this account to start the workloads in rootless mode. For a workload to mount a host mountpoint to the container, it first needs the `flotta` host user to have access to the device. 

This can be achieved by adding the device's group as a supplementary group to the `flotta` user. In case of a webcam, the group is `video`:

```shell
[root@fedora ~]# ls -la /dev/video2
crw-rw----. 1 root video 81, 2 Jul 22 16:14 /dev/video2
```

And adding the supplementary group is a simple command:
```shell
[root@fedora ~]# usermod -a -G video flotta
```
Since we have changed the flotta group list, we will restart the systemd user service that hosts the podman instance running with the `flotta` user. This change is required to propagate the changes to the running proceses under the `flotta` account:

```shell
[root@device ~]# systemctl restart user@$(id flotta -g).service
```

Adding the supplementary group will allow the `flotta` user to access the device from a file system perspective, but we need to enable the access to the containers. For that purpose we have to make additional adjustments to the workload.

## Keep the groups in the container ##

Adding the supplementary group `video` to the `flotta` user will clear the access to the device from a filesystem perspective. But since the workloads run in a container, we also need to look at how to instruct the container runtime to use the same groups from the `flotta` user in the container's user so that the host file system allows access from the user running inside the container. For security reasons, the user id and group id running inside the container is different than the one in the host.

Propagating the groupIds enables container processes access to host files without being blocked by the host's file system due to invalid access rights. To do so, Flotta leverages on a feature from the `crun` runtime container that, when used, instructs the runtime to keep the same group Ids from the user's host to the container. In Flotta this feature is eanbled by defining in your workload the following annotation `podman/run.oci.keep_original_groups: "1"`:

```
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeWorkload
metadata:
  name: webcam
  annotations:
    podman/run.oci.keep_original_groups: "1"
spec:
...
...

```

## Facing SELinux ##
With SELinux enabled by default, rootless containers have further restrictions to access the host file system. For mounted devices this is no different. There are two approaches on how to allow a workload to access a mounted device with SELinux's blessings:

* Define the SELinux rules specific for the mounted device
* Use the `seLinuxOptions` in the pod's `spec` field to instruct the runtime to define the type as `spc_t` to what is in essence disabling SELinux in the container. Since we are running a rootless container, the security impact is limited to what the `flotta` user is able to do. [Here](https://danwalsh.livejournal.com/74754.html) is a detailed explanation of what it is and can do for those initiated in the art of container runtime.

Let's see them in more detail:

### Defining the SELinux rules specific for the device ###
The process is to run the workload and identify the missing SELinux rules that prevent the workload from operating the device and finally configure SELinux to add the new rules. The process relies on the `audit2allow` utility to capture the denial attempts in `/var/log/audit/audit.log` and generate the rules to allow the access.

The following rules are an example of the outcome of running the `audit2allow` utility after various attempts to run a workload that interacts with a webcam:

```shell
module v4linux 1.0;

require {
	type v4l_device_t;
	type container_t;
	class chr_file { getattr ioctl map open read write };
}

#============= container_t ==============

#!!!! This avc can be allowed using the boolean 'container_use_devices'
allow container_t v4l_device_t:chr_file { getattr ioctl open read write };
allow container_t v4l_device_t:chr_file map;
```

In some cases, setting the `container_use_devices` boolean to true in SELinux (`setsebool container_use_devices on`) might be sufficient to allow containers from interacting with the devices. As you can see in the example above, additionally to the operations allowed by the boolean of `getattr`, `ioctl`, `open`, `read` and `write`, the `map` action is also required in the case of the webcam.

The downside of this approach is that requires additional configuration changes to the device and also to run the workload a few times until the correct rules have been generated, but when achieved it can be used to configure all hosts with the same device as part of the onboarding and configuration process even before installing Flotta. From a security perspective it can be an appealing option.

### The Super Privileged Container ###
For those who want a more straight forward approach and don't want to mess with SELinux rules for each device, there is a special SELinux label type named `Super Privilege Container` or `spc_t` that in essence it disables SELinux in the container. Here is an example of a workload that accesses a webcam and uses this type to overcome the different SELinux types between the process running in the container and the device.

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeWorkload
metadata:
  name: webcam
  annotations:
    podman/run.oci.keep_original_groups: "1"
spec:
  deviceSelector:
    matchLabels:
      app: webcam
  type: pod
  pod:
    spec:
      containers:
      - image: quay.io/jordigilh/ffmpeg:latest
        name: fedora
        volumeMounts:
        - mountPath: /dev/video2
          name: video
        securityContext:
          seLinuxOptions:
            type: 'spc_t'
      restartPolicy: Always      
      volumes:
      - name: video 
        hostPath:
          path: /dev/video2
          type: File
```

