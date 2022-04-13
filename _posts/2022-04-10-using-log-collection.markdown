---
layout: post
title:  "Log Collection on Flotta devices"
date:   2022-04-10 12:00:00 +0100
categories: flotta
author: Eloy Coto <eloycoto@acalustra.com>
tags:
  - guide
  - flotta
  - logs

summary-1: Introduction to flotta log collection
---

When running thousands of devices on the far edge, log collection retrieval may
differ from one site to another, as also the limit of data that can be sent
from the device or stored in the device.

At the same time, workload logs can vary in terms of importance, so the backup
workload logs maybe need to be always pushed, and maybe another workload with
less importance can lose logs on network connectivity issues. At the same time,
maybe you don’t want workload that manages any personal information to send
information outside the country.

For that, Flotta introduces log collection targets, so each device - or
deviceSets- will have a set of custom logs servers that one workload can use to
send the logs to.

![Device Logs diagram](/assets/images/DeviceLogsConfig.png)

The main use case is to be able to define servers in edge devices and these
servers to be consumed by the workloads; this way user roles are very well
defined - edge-administrators define the servers and developers use the given
values.

*A sample workflow for a retail store can be:*

**Edge Device Administrator:** defines the device security, heartbeat and
general options based on the device or deviceSet. In this case, will define two
kinds of logs servers, LogSecure which always pushes the logs to the server,
with big storing buffers. At the same time, there is a logGeneral, that is the
server that may lose logs on network downtime, or maybe using different
transports.

**Edge developer:** In this case, the developer knows that for running the
workload in all stores, there are always two kinds of log servers that can be
used, because Edge Administration shared all the details about buffer, quotas
and destination.

To collect logs, a subprocess reads the workloads stdout and pushes it to a
buffer, even if the device is disconnected from network for a while, it’ll push
the right timestamp to the server, due to the buffer being aware of the log was
retrieved. When the buffer is full, some logs will be dropped to avoid filling
the RAM on the device.

Regarding transports, at the moment, the Flotta device agent only supports raw
Syslog transport, but in the following releases, new transports will be added,
like Loki, Kafka, Elastic and MQTT.

## Example setup

It's quite easy to setup an edge device; in case of Syslog, the following
config-maps should be in place:

```
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: dc1-syslog
  namespace: default
data:
  Address: dc1.syslog.project-flotta.io:601
  Protocol: tcp
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: secure-syslog
  namespace: default
data:
  Address: secure.dc1.syslog.project-flotta.io:601
  Protocol: tcp
```


Per each device, the following `logCollection` attribute should be added:
```
—--
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDevice
metadata:
  name: e5f44cc8ddfb408a9b85f54c0c3efa02
  namespace: default
spec:
  requestTime: "2022-03-23T11:40:59Z"
  logCollection:
   dc1-syslog:
     bufferSize: 10
     kind: syslog
     syslogConfig:
       name: dc1-syslog
   secure-syslog:
     bufferSize: 100
     kind: syslog
     syslogConfig:
       name: secure-syslog
```



So, dc1-syslog will only store 10Mb of logs in the buffer, meanwhile dc1-syslog
can submit much bigger logs and make sure that logs are not dropped.

## Edge Deployment setup

At the edgedeployment, the following information should be added:

```
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeWorkload
metadata:
  name: random-workload
spec:
  logCollection: dc1-syslog
  deviceSelector:
    matchLabels:
      app: foo
  type: pod
  pod:
    spec:
      containers:
        - name: random-server
          image: docker.io/eloycoto/logexample
```

And for secure syslog server can be the following:

```
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeWorkload
metadata:
  name: payment-workload
spec:
  logCollection: secure-syslog
  deviceSelector:
    matchLabels:
      app: foo
  type: pod
  pod:
    spec:
      containers:
        - name: random-server
          image: docker.io/eloycoto/payments:v1
```

So each deployment will use the log collection given by the edge-administrator.
