---
layout: documentation
title: Flotta use cases
---

## Retail

Flotta is great for retail industries, where Flotta can be used to manage all
Point of sale devices from a single Kubernetes instance. At the same time, due
to the low footprint, it can be used as kiosk mode.

## IoT

When running multiple IoT devices, the power consumption is a key element,
flotta-device worker uses to track power consumption over time and try to keep
the resource usage as small as possible to be able to run any IoT workload where
power can be provided by a small solar panel.

At the same time, Flota is designed for non-reliable networks, so any
low-bandwidth connection (GPRS, LoraWAN, NB-IoT) will work without issues.

## IA edge

IA on the edge is a has tons of posibilities, Flotta device agent is available
on ARM or x86, also has support for any kind of Nvidia Jetson boards, the main
boards for IA in the edge.
