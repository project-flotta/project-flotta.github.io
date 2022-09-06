---
layout: post
title:  "Flotta Image Classification tool for edgedevices"
date:   2022-08-27 11:44:17 +0530
categories: flotta
author: Deependra Singh Shekhawat
tags:
  - guide
  - flotta
  - image-classification
  
summary-1: Getting started with Flotta Image Classification Tool
---
The ability to detect objects is essential in a number of fields, including computer vision, robotics, and autonomous driving. With the idea of applying real-time object identification on edge devices with low inference time and high accuracy, many approaches to object detection can hardly operate on the resource-constrained edge devices.

The Flotta Image Classification tool overcomes the aforementioned limitations, by delivering amazingly precise object detection while enabling faster object detection on edge devices (like Raspberry Pi, etc.)

>Workload Dependencies -
>  - Python >=3.7
>  - OpenCV 4.6

>Device configuration (at least) -
> - CPU 1GHz
> - Memory 1024MB
> - Disk Space 2GB

## Prerequisite
- Flotta-configured device. (see [documentation](https://project-flotta.io/documentation/v0_2_0/intro/overview.html))

## Getting Started

**Project repository can be found [here](https://github.com/dpshekhawat/image-classification).**

### Preparations
As part of the flotta installation, prioritizing security of containers we create the user flotta and utilise that user to execute the tasks.
By default, the flotta user does not have access to any mounted devices, thus we must first make changes to provide flotta user access to the device in /dev before configuring the runtime to permit the access.

```shell
#video group access to flotta user 
[root@device ~]# usermod -a -G video flotta

#expected
[root@device ~]# id flotta
uid=1001(flotta) gid=1001(flotta) groups=1001(flotta),39(video)
```

Following device registration, to run our workload on specific device, we need to label the device -

Use following command to add the label:
```shell
kubectl label edgedevice <device CR name> app=camera
```

Confirm that you have an EdgeDevice labelled with app=camera
```shell
$ kubectl get edgedevice -l app=camera
NAME                                          AGE
ff8612a5bd1a40cca403ac1fc95cc2ad              3m
```
Now we will define the manifests using the same label.

**Next**, you will need a webcam mounted to your workload or else it fails with no device connected. Change the device id from 0 to 1/2/3... specific to your device.

Using the webcam in my system as an example mounted in /dev/video0. Make sure you specify them in the `edgeworkload.yaml` - 
```yaml
volumemounts:
 - mountPath: /dev/video0
   name: video
```
(and here)
```yaml
volumes:
- name: video 
  hostPath:
    path: /dev/video0
    type: File
```

### Storage
Specified in `edgedevice.yaml`.
```yaml
storage:
    s3:
      secretName: s3secret # secret containing S3 API access credentials
      configMapName: s3config # configmap containing S3 API access configuration options
```
>The default directory `"../export/images/"` is used for saving images.

Note: Any path that you specify in data sync configuration should be placed under /export in the container.
```yaml
data:
    egress:
      - source: images # container folder under /export
        target: images # object storage bucket folder
```
> Note: Data is synced every 15 seconds.

### Deploy
First deploying the `configmaps.yaml` and `secrets.yaml` manifests following `edgedevice.yaml` then finally `edgeworkload.yaml`.

Let’s monitor EdgeDevice object in our cluster to see when the device becomes available:
```shell
$ watch -t kubectl get edgedevice ff8612a5bd1a40cca403ac1fc95cc2ad -ojsonpath="{.status.workloads}"
```
it should show our workload -
```
[{"lastTransitionTime":"2022-08-28T16:03:51Z","name":"edge-ic-workload","phase":"Running"}]
```
(if showing `deploying` phase, wait for a while as the image is being pulled)


### Controls (START/STOP)
1. Using environment variable in `configmaps.yaml` -
```yaml
data:
  CAPTURE: "True" # starts detection 
```
Setting `CAPTURE: "False"` will stop the camera but keep the workload running.
```shell
$ kubectl apply -f configmaps.yaml
```
2. (OR) Removing the workload from the device using -
```shell
$ kubectl delete -f edgeworkload.yaml
```

### Output -

SSH to the device and become the flotta user to access the container and see that the images were created -

```shell
[root@fedora]$ sudo su -l flotta -s /bin/bash -c "podman exec -it edge-ic-workload-edge-ic-workload ls ../export/images/"
2022-08-29_17-32-58.jpeg      2022-08-29_17-33-03.jpeg
2022-08-29_17-32-58.json      2022-08-29_17-33-03.json
```
Using json for keeping track of detected objects specific to images -
```json
{"title": "2022-08-29_17-32-58", "detected": ["tvmonitor", "laptop", "keyboard"]}
```
> Note: Remember that the files are only produced when an object is found, thus if none are produced, this might be the case.

### Configurable parameters 

```yaml
data:
  CAPTURE: "True"
  THRES: "0.25"
  TIMEINT: "5"
```
| Parameter | Description| Data type and Constraints | Default/Suggested value |
|---|---|---|---|
| CAPTURE | boolean flag to enable/disable capture | bool | True |
| THRES | Boxes with a confidence score less than confidence threshold are discarded  | float | >=0.25 |
| TIMEINT | time interval for detection | int | 5 |


## Workflow 
![Workflow](/assets/images/flotta_image_classification-workflow.png)

Once the edge device is configured, it begins real-time object recognition on the camera feed at the specified time interval and if an object is detected it captures and stores the images with the localization of those objects. 

The functionality of the Flotta agent and Operator of bidirectional data sync between the device and storage is then used to sync these images from the device with object storage. (learn more on Data Synchronization [here](https://project-flotta.io/documentation/v0_2_0/operations/data_synchronization.html))

Next the images can be browsed using flotta web app running in a cluster.

(*Quick tip*: Click on the images for expanded view)

Some example images detected using Flotta Image Classification Tool [here](http://www.youtube.com/watch?v=RHNfVsw2V7E).

Please file any issues or propose new ideas at [GitHub Issues](https://github.com/dpshekhawat/image-classification/issues)