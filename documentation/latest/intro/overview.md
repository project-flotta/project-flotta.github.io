---
layout: documentation
title: What is flotta
---

## Fleet management for edgedevices

Flotta adds a way to manage all your fleet of devices from a single point, in
this case, using Kubernetes CRD to handle all kinds of device configurations.

Each Edgedevice can register, pull configuration using the Fleet Management API
and keep syncing the data using a secure MTLS protocol between the device and
the Fleet Management API.

At the same time, you can schedule a container workload to run in the device
using a Workload CRD, where a container workload can be scheduled for an
unlimited number of devices.

### Fleet observability

Running container workloads in the edge device is the first part, but at the
same time, the Device control plane takes care of the following actions in the
workload to make edge-administration life easier.

  - Get metrics from workloads and push to a remote serve when the connectivity is
    up.
  - Get logs from workloads and push to a remote server when the connection is up.

### Device configuration

Device configuration is a hard part on edge, this is why Flotta trusts
RPM-Ostree technology to run updates on the non containerized workloads.

At the same time, each device can be configured at a single unit - where all
observability, logs, heartbeats can be set- or can be defined on DeviceSets. This
CRD allows configuring multiple edgedevices from a single unit, making easier
the edge-administration life.

Because all the process is based on Kubernetes CRD, it is compatible with your
favourite GitOps tools, so deploy pipelines can be defined across all of your
fleet.

## Os Lifecycle

@TODO TBC
