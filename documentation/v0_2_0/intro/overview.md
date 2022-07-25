---
layout: documentation
title: What is flotta
---

## Edge Devices Management For k8s Workloads

Flotta adds a way to manage all your edge devices from a single point using
Kubernetes CRD to handle all kinds of device configurations.

Each edge device can register, pull configuration using the Flotta Edge API and
keep syncing the data using a secure MTLS protocol between the device and the
Flotta Edge API.

It is also possible to schedule a container workload to run in the device using
a Workload CRD. A container workload can be scheduled for an unlimited
number of devices.

{% plantuml %}
@startuml
!theme bluegray
skinparam dpi 65
skinparam backgroundColor transparent
skinparam shadowing false
skinparam defaultFontName DejaVu Serif
skinparam defaultFontSize 16
left to right direction

node "Edge Cluster" {
    frame Kubernetes {
        database etcd [
            ETCD
            ====
            EdgeDevice
            EdgeDeviceSet
            EdgeWorkload
            ----
        ]
        component "API Server" as apiserver
        component "Flotta Edge API" as edgeAPI
        component "Flotta Operator" as operator
    }
}

node "Edge Device" {
    frame "Flotta Agent" as deviceAgent {
        component "Device Worker" as device_worker
        component "Podman" as podman
        component "Systemd" as systemd
        component "Workloads" as workloads
    }
}

device_worker -r-> edgeAPI : Gets\nupdates/\nSends\nstatus\n[https]

operator <--> apiserver: reconcile
edgeAPI <--> apiserver: register/\nupdate device
apiserver <--> etcd: "Flotta CRDs"

device_worker --l--> podman : interacts with
podman --> systemd : Generates
device_worker --> systemd : Configures
systemd --> workloads : Runs

@enduml
{% endplantuml %}

### Edge Devices Observability

Device agents takes care of running container workloads, but at the same time,
it also takes care of the following actions in the workload to make
edge-administration life easier.

  - Get metrics from workloads and push to a remote serve when the connectivity is
    up.
  - Get logs from workloads and push to a remote server when the connection is up.

### Device Configuration

Device configuration is a hard part on edge, this is why Flotta trusts
RPM-OSTree technology to run updates on the non containerized workloads.

Each device can be configured as a single EdgeDevice CR - where all
observability, logs, heartbeats can be set - or can be defined on DeviceSets CR.
This grouping CRD allows configuring multiple edgedevices from a single unit,
making easier the edge-administration life.

Because all the process is based on Kubernetes CRD, it is compatible with your
favourite GitOps tools, so deploy pipelines can be defined across all of your
edge devices.

## OS Lifecycle

@TODO TBC
