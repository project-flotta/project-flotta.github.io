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

>The default directory `"../export/images/"` is used for saving images.


### Workflow 
![Workflow](/assets/images/flotta_image_classification-workflow.png)

Once the edge device is configured, it begins real-time object recognition on the camera feed at the specified time interval and if an object is detected it captures and stores the images with the localization of those objects. 

The functionality of the Flotta agent and Operator of bidirectional data sync between the device and storage is then used to sync these images from the device with object storage. ( learn more on Data Synchronization [here](https://project-flotta.io/documentation/v0_2_0/operations/data_synchronization.html). )

Next the images can be browsed using flotta web app running in a cluster.

Some example images captured using Flotta Image Classification Tool [here](http://www.youtube.com/watch?v=RHNfVsw2V7E).

Please file any issues at [GitHub Issues](https://github.com/dpshekhawat/image-classification/issues)