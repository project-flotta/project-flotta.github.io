---
layout: post
title:  "Edge Example App: Sense the Internet Part 2"
date:   2022-09-05 03:27:05 +0100
categories: flotta
author: Ahmad Ateya <ahmad.m.ateya@gmail.com>
tags:
- flotta
- devices
- workloads
- gsoc

summary-1:
---
Edge Example App is an app for Flotta Edge devices, with a workload that will be deployed on the device that has two main features:
- Sensing the Internet (which helps to construct devices network topology). <= this article (Part 2)
- Read CPU temperature (which indicate how much load the device is handling).

## How this app works
This app is the presenting layer of the Flotta Edge devices, get its data from the [backend app](https://github.com/project-flotta/flotta-webapp-backend) endpoints and display it to the user.

You can list all devices that uses your S3 Bucket as storage bucket, and for each device you can see its information and its network topology.

Here are screenshots of the app:

- List Devices page

<img src="/assets/images/list-devices-page.png" alt="List devices" width="800"/>

- Device page with app features

<img src="/assets/images/device-features-page.png" alt="List devices" width="800"/>

- Network topology page

<img src="/assets/images/network-topology-page.png" alt="List devices" width="800"/>

## How to use this app
The [backend app](https://github.com/project-flotta/flotta-webapp-backend) is the only requirement, so deploy the backend app, check [here](https://github.com/project-flotta/flotta-webapp-backend#getting-started), and then you're ready to deploy this app, check [here](https://github.com/project-flotta/flotta-webapp-frontend#getting-started).

All you need have to use this app is to have S3 bucket to store the data, and to configure the backend app to use this bucket.

## Future work ideas
- Add more filters to the Network Topology graph (e.g. by date etc.).
- Add more information to the devices list (e.g. device type, device location etc.).

## GitHub Repositories
- [https://github.com/project-flotta/flotta-edge-example](https://github.com/project-flotta/flotta-edge-example) <= Device App
- [https://github.com/project-flotta/flotta-webapp-frontend](https://github.com/project-flotta/flotta-webapp-frontend) <= Web App frontend
- [https://github.com/project-flotta/flotta-webapp-backend](https://github.com/project-flotta/flotta-webapp-backend) <= Web App backend