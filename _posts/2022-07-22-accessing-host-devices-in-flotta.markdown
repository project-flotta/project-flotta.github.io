---
layout: post
title:  "Accessing host devices in Flotta"
date:   2022-07-22 12:00:00 +0100
categories: flotta
author: Jordi Gil <jgil@redhat.com>
tags:
  - podman
  - rootless
  - devices
  - webcam

summary-1: Accessing host devices in Flotta
---

In today's container security, it is important to reduce the risk of a security breach in a container that can escape from the container runtime and put the device at risk. One way to reduce such risks is to run the container with a non-root user, so that if there is such spill the attacker won't be able to gain access to root level privileges. These type of containers are what is called rootless containers.

Rootless containers also limit the access to the host devices by default, as it depends on the privileges of the runtime user access. In Flotta we create the user `flotta` as part of the flotta rpm installation and run the workloads with that user. By default the flotta user does not have access to any mounted device (unless configured otherwise by the OS), so we have to make changes first on granting file access to `flotta` to the device in `/dev`, and then configuring the runtime to enable the access.

To demonstrate the ability to interact with a host device, I will use the webcam in my laptop as an example. The webcam is mounted in `/dev/video2` with the following file system atrributes:

```shell
[root@device ~]# ls -la /dev/video2
crw-rw----+ 1 root video 81, 2 Jul  22 11:30 /dev/video2
```

I have built a container from a fedora 36 image that runs the `ffmpeg` application and captures a screenshot from the webcam on a 10 seconds interval:

```shell
#!/bin/sh

rm -Rf /tmp/helloworld-?.jpg
for i in {1..10}; do
  echo Taking snapshot
  /usr/bin/ffmpeg -f video4linux2 -s 640x480 -i /dev/video2 -ss 0:0:2 -frames 1 /tmp/helloworld-$i.jpg
  echo Sleeping 10 seconds
  /usr/bin/sleep 10
done
ls -la /tmp/helloworld-?.jpg
sleep infinity
```

And here are the contents of the `Dockerfile`:

```shell
FROM registry.fedoraproject.org/fedora:36
RUN dnf install -y ffmpeg-free
COPY script.sh /script.sh
ENTRYPOINT ["/script.sh"]
```

## Configuing the host to capture images from a webcam ##


The device is read/write for `root` and members of the `video` group. Let's check what are the `flotta` user group information:

```shell
[root@device ~]# id flotta
uid=1000(flotta) gid=1000(flotta) groups=1000(flotta)
```

There is no `video` supplementary group attached to `flotta`. If I want `flotta` to access this device, I need first to add the supplementary group `video` to `flotta`:

```shell
[root@device ~]# usermod -a -G video flotta
```

And now the `flotta` user has access to the `video` group:

```shell
[root@device ~]# id flotta
uid=1001(flotta) gid=1001(flotta) groups=1001(flotta),39(video)
```

Now I need to restart the flotta user service process to be aware of the group changes, otherwise the new group will not be reflected in the containers:

```shell
[root@device ~]# systemctl restart user@$(id flotta -g).service
```

## Defining the workload ##

At this step I have ensured that `flotta` as a user in the host has access to the webcam. Now I need to guarantee that the container is also able to share the same privileges. To that I will leverage on the annotation `run.oci.keep_original_groups=1`, supported by the `crun` container runtime, that allows containers to inherit the running user's groups. 


### Annotating the workload ###
Starting from podman 4.1.0, it is possible to add annotations when running pod workloads. These annotations are then propagated to the underlying container runtime. The Flotta operator propagates annotations to the device agent when defined in the `EdgeWorkload` with the `podman/` prefix. More precisely, it removes the prefix `podman/` from the annotation key name and propagates the remaining name and value.

### Configuring the pod security context for SELinux ###
As a security measure, SELinux prevents the container from accessing the device because the types mismatch. If I try to access `/dev/video2` from a container, SELinux will not allow me:

```shell
AVC avc:  denied  { read write } for  pid=2393 comm="ffmpeg" name="video2" dev="devtmpfs" ino=515 scontext=system_u:system_r:container_t:s0:c56,c580 tcontext=system_u:object_r:v4l_device_t:s0 tclass=chr_file permissive=0
```

The source type is `container_t` and the target type is `v4l_device_t`.  

To solve this there are 2 options:
* Configure SELinux to add the rules that allows container types to access the webcam type (see notes section for more detail).
* Use the Super Privileged Container type `spc_t` in the pod's `securityContext` section. This [container type](https://danwalsh.livejournal.com/74754.html) disables SELinux in the container. Since we are running a rootless container, the security impact is limited to what the `flotta` user is able to do. [Here](https://developers.redhat.com/blog/2014/11/06/introducing-a-super-privileged-container-concept) is more detailed explanation of what it is and can do for the those hungry with knowledge.


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

In this example we are mounting the host device `/dev/video2` to the container's equivalent `/dev/video2`. Be aware that your webcam location might be in a different device number, so best to identify which one before running the workload and change the scripts accordingly.

## Running the workload ##

At this point, we are ready to deploy the workload on the device. For this example, I have created a VM running fedora and attached the webcam in my laptop on `/dev/video2`. I have labeled my edge device with `app=webcam` to make sure that the Flotta controller schedules the workload on this specific device.

```shell
[jgil@fedora ~]$ kubectl create -f workload_webcam.yaml
```

Now let's make sure that the workload is running by inspecting the status in the edgedevice:



```shell
[jgil@fedora ~]$ kubectl get edgedevice/4cc27d11334f4242baa7efc795d2bbc0 -ojsonpath="{.status.workloads}"| jq .
[
  {
    "lastTransitionTime": "2022-07-14T14:50:28Z",
    "name": "webcam",
    "phase": "Running"
  }
]
```

Since I'm running this on a VM, I'm going to ssh to the device and become the `flotta` user to access the container and see that the images were created:

```shell
[jgil@fedora ~] ssh -l root 192.168.122.23
[root@fedora ~]# su -l flotta -s /bin/bash -c "podman exec -it webcam-fedora ls -lart /tmp"
total 112
dr-xr-xr-x. 1 root root   54 Jul 22 15:02 ..
-rw-r--r--. 1 root root 8078 Jul 22 15:02 helloworld-1.jpg
-rw-r--r--. 1 root root 8078 Jul 22 15:02 helloworld-2.jpg
-rw-r--r--. 1 root root 8068 Jul 22 15:02 helloworld-3.jpg
-rw-r--r--. 1 root root 9172 Jul 22 15:03 helloworld-4.jpg
-rw-r--r--. 1 root root 8786 Jul 22 15:03 helloworld-5.jpg
-rw-r--r--. 1 root root 8699 Jul 22 15:03 helloworld-6.jpg
-rw-r--r--. 1 root root 8892 Jul 22 15:03 helloworld-7.jpg
-rw-r--r--. 1 root root 8981 Jul 22 15:03 helloworld-8.jpg
-rw-r--r--. 1 root root 9358 Jul 22 15:04 helloworld-9.jpg
-rw-r--r--. 1 root root 9414 Jul 22 15:04 helloworld-10.jpg
drwxrwxrwt. 1 root root 4096 Jul 22 15:04 .
```

There we have the 10 images inside the container. As an exercise, you can enhance this example by adding a data sync path to upload the images to a remote S3 storage using the data transfer capabilities of the Flotta agent. This way you won't need to sneak into the VM like I did to see that the images were created.

## Conclusion ##

Flotta is gradually improving the support of workloads that can run on devices without compromising the security of the device. With Flotta it is possible to run workloads that generate and consume data and are capable of synchronizing with a remote compatible S3 storage, as well as workloads that require access to the host mounted devices, such as webcams or sensors.

There is still room for improvement in the usability with the ability to configure the supplementary groups without having to remote to the device each time. We hope in the next releases we can provide a mechanism to configure the host in these areas in a declarative manner. Feel free to drop suggestions or enhancements to the [project](https://github.com/project-flotta/flotta-operator/issues) in the github repository!.

## Notes ##

In the case of my webcam, I was able to add the specific rules to SELinux to allow the `container_t` type to access the `v4l_device_t` type, which is the label type that is used by `/dev/video2`:

```shell
[root@fedora ~]# ls -laZ /dev/video2
crw-rw----. 1 root video system_u:object_r:v4l_device_t:s0 81, 2 Jul 22 09:39 /dev/video2
```

The easiest way to identify the SELinux missing rules is using `audit2allow`. This utility analyzes the information in `/var/log/audit/audit.log` and generates the SELinux policies based on denied operations. In my case, I had to run the workload a few times until I was able to get all the rules.

The utility created the following rules:

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

To create the package for the rules rules you can either use the `audit2allow -a -M <modulename>.pp` command, or you use the following commands for a step by step execution:

Store the contents of the rules in a file named `v4linux.te` in the device's `/tmp`

```shell
[root@fedora ~]# cat >/tmp/webcam.te <<EOF
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
EOF
```

Now convert it to a policy module:

```shell
[root@fedora ~]# checkmodule -M -m /tmp/v4linux.te -o /tmp/v4linux.mod
```

And generate the package:

```shell
[root@fedora ~]#  semodule_package -o /tmp/v4linux.pp -m /tmp/v4linux.mod
```

Finally install it:

```shell
[root@fedora ~]# semodule -i /tmp/v4linux.pp
```

Now SELinux is configured to allow the container to interact with the webcam. To test this, I deploy a new workload that does not have the `seLinuxOptions` defined in the pod spec:

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeWorkload
metadata:
  name: webcam-nosecuritycontext
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
      restartPolicy: Always      
      volumes:
      - name: video 
        hostPath:
          path: /dev/video2
          type: File
```

Checking the status of the workload we get a satisfactory `Running`:

```shell
[jgil@fedora ~]$ kubectl get edgedevice/4cc27d11334f4242baa7efc795d2bbc0 -ojsonpath="{.status.workloads}"| jq .
[
  {
    "lastTransitionTime": "2022-07-22T15:02:28Z",
    "name": "webcam",
    "phase": "Running"
  },
  {
    "lastTransitionTime": "2022-07-22T15:31:28Z",
    "name": "webcam-nosecuritycontext",
    "phase": "Running"
  }
]
```

And finally, checking the contents of the `/tmp` directory we can see the images stored:

```shell
[jgil@fedora ~] ssh -l root 192.168.122.23
[root@fedora tmp]# su -l flotta -s /bin/bash -c "podman exec -it webcam-nosecuritycontext-fedora ls -lart /tmp"
total 84
dr-xr-xr-x. 1 root root   42 Jul 22 15:30 ..
-rw-r--r--. 1 root root 7849 Jul 22 15:30 helloworld-1.jpg
-rw-r--r--. 1 root root 7730 Jul 22 15:31 helloworld-2.jpg
-rw-r--r--. 1 root root 7732 Jul 22 15:31 helloworld-3.jpg
-rw-r--r--. 1 root root 7743 Jul 22 15:31 helloworld-4.jpg
-rw-r--r--. 1 root root 7782 Jul 22 15:31 helloworld-5.jpg
-rw-r--r--. 1 root root 7868 Jul 22 15:32 helloworld-6.jpg
-rw-r--r--. 1 root root 7839 Jul 22 15:32 helloworld-7.jpg
-rw-r--r--. 1 root root 7822 Jul 22 15:32 helloworld-8.jpg
-rw-r--r--. 1 root root 7725 Jul 22 15:32 helloworld-9.jpg
-rw-r--r--. 1 root root 7754 Jul 22 15:32 helloworld-10.jpg
drwxrwxrwt. 1 root root 4096 Jul 22 15:32 .
```