---
layout: documentation
title: Flotta use cases
---

## Retail

Flotta is great for retail industries, where Flotta can be used to manage all
Point of sale devices from a single Kubernetes instance. At the same time, due
to the low footprint, it can be used as kiosk mode.

[![](/assets/images/retail_diagram.png){:width="600px"}](/assets/images/retail_diagram.png)

## IoT

When running multiple IoT devices, the power consumption is a key element,
flotta-device worker uses to track power consumption over time and try to keep
the resource usage as small as possible to be able to run any IoT workload where
power can be provided by a small solar panel.

At the same time, Flota is designed for non-reliable networks, so any
low-bandwidth connection (GPRS, LoraWAN, NB-IoT) will work without issues.

## AI edge

AI on the edge has tons of posibilities, Flotta device agent is available on ARM
or x86, also has support for any kind of Nvidia Jetson boards, the main boards
for AI in the edge.

## Industry

When a factory with thousands of different sensors, robotics arms, and multiple
computers that needs to run each one a different workload, flotta provides a way
to manage all these devices from a single user place.

![](/assets/images/manufacture_line.png)
