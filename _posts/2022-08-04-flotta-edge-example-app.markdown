---
layout: post
title:  "Flotta Edge Example App: Sense the Internet Part 1"
date:   2022-08-04 03:27:05 +0100
categories: flotta
author: Ahmad Ateya <ahmad.m.ateya@gmail.com>
tags:
  - flotta
  - devices
  - workloads

summary-1: 
---
Edge Example App is an app for Flotta Edge devices, with a workload that will be deployed on the device that has 2 main features:
- Sensing the Internet (which helps to construct devices network topology). <= this article
- Read CPU temperature (which indicate how much load the device is handling).

As Project Flotta goal is to manage workloads deployed on small-footprint devices and dealing with network connectivity issues, this app provides a way of collecting network information that will be exported to the edge cluster.
this App Along with the Web UI Interface, provides a good view of the network topology and the devices that are connected to the devices network.

## How this app works
taking the simple way of getting network information, this app collects its information about the network by sending a packet on the IP network to the Edge Cluster, calculating the time taken for each hop the packet makes during its route to the destination, this much like traceroute in the network but done on the device.

![](/assets/images/traceroute.png)

as a workload app, this app benefits from Flotta Edge devices architecture, collecting its information and saving it to a file on the device and let the device worker send it to the edge cluster, this way


## How to use this app

After registering your device, use the following manifest to deploy the app:

// TODO add the manifests here
```yaml

```

### Github Repository
- link to github repo
