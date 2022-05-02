---
layout: documentation
title: Flotta vs others
---

Flotta is designed for the micro-edge, where no high-availabilty is needed and
edgedevice does not need to have a control-plane API at all.

## Flotta vs Microshift

Microshift provides a way to use the Kubernetes API inside the EdgeDevice, it
also has options to run in high-availabilty mode where you can add multiple
nodes. Microshift is a single-container workload.

Flotta integrates nicely with Microshift, where Flotta manages the OS lifecycle
and the Microshift workload, and Microshift provides a kubernetes API to manage
edgedevices workloads and a full set of kubernetes features.
