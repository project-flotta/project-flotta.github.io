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

The Flotta Image Classification tool overcomes the aforesaid limitations, by delivering amazingly precise object detection while enabling faster object detection on edge devices (like Raspberry Pi, etc.)

>Dependencies -
>  - Python >=3.7
>  - OpenCV 4.6

## Prerequisite
- Flotta-configured device.

## Getting Started
Some example images captured using Flotta Image Classification Tool [here](http://www.youtube.com/watch?v=RHNfVsw2V7E)

### Configurable parameters (default)

- `THRES = 0.25` _confidence threshold currently 25%_
- `TIMEINT = 5` _timeinterval for capturing every 5 secs_
- `CAPTURE = True` _start capturing if True_

The default directory `"images/"` is used for saving images.


## Workflow 
The workload is first deployed on the edgedevice once it has been configured using Flotta operator. 
( Checkout how to configure device with flotta [here](https://project-flotta.io/flotta/2022/04/15/flotta-and-raspberry-pi.html#installation) )

Following that, once the edge device is operational, it begins real-time object recognition on the camera feed and stores images at the specified intervals. 

The functionality of the Flotta agent and Operator of bidirectional data sync between the device and storage is then used to sync these images with object storage. ( learn more on Data Synchronization [here](https://project-flotta.io/documentation/v0_2_0/operations/data_synchronization.html). )

Now images are presented on the Flotta Webapp while on the backend  the images are retrieved from the storage.