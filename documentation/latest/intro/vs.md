---
layout: documentation
title: Flotta vs others
---

Flotta is designed for the micro-edge, where no high-availabilty is needed and
edgedevice does not need to have a control-plane API at all. At the same, it is
using a pull model, so no open connection is needed on your device.

## Flotta vs Microshift

Microshift provides a way to use the Kubernetes/Openshift APIs inside the
EdgeDevice, where all CRUD operations need to be performed using that APIServer.
On the ohter hand, Microshift has a way to have more than one node in one edge
location, where small edge cluster can be used for different workloads. 

Flotta integrates nicely with Microshift, where Flotta manages the OS lifecycle
and the Microshift workload, and Microshift provides a kubernetes API to manage
edgedevices workloads and a full set of kubernetes features.
