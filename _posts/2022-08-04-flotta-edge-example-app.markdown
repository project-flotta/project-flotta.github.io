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
Use the following manifests to deploy the app to your device:

#### First apply your secrets and configmaps:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: s3secret
  namespace: default
type: Opaque
data:
  AWS_ACCESS_KEY_ID: <your-aws-access-key-id>
  AWS_SECRET_ACCESS_KEY: <your-aws-secret-key>
```

```yaml
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
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: s3config
  namespace: default
data:
  BUCKET_HOST: play.min.io
  BUCKET_NAME: flotta-data-bucket
  BUCKET_PORT: "443"
  BUCKET_REGION: us-east-1
```

#### Second apply the device by this manifest (or update it if it already exists):

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDevice
metadata:
  name: <your-device-name>
  namespace: default
  labels:
    app: <some-label-here>
spec:
  requestTime: "2022-07-14T04:55:44Z"
  logCollection:
    dc1-syslog:
      bufferSize: 10 # 10 megabytes of size
      kind: syslog
      syslogConfig:
        name: dc1-syslog
    secure-syslog:
      bufferSize: 100 # 100 megabytes of size
      kind: syslog
      syslogConfig:
        name: secure-syslog
  storage:
    s3:
      configMapName: "s3config"
      secretName: "s3secret"
```

> Note: these files explained in the [Docs](https://project-flotta.io/documentation/v0_2_0/operations/data_synchronization.html#configuring-edgedevice)

#### Finally, apply the app to the device:
```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeWorkload
metadata:
  name: <workload-name>
spec:
  logCollection: dc1-syslog
  deviceSelector:
    matchLabels:
      app: <device-label> # same as the device label
  type: pod
  pod:
    spec:
      containers:
        - name: edge-example-workload
          image: docker.io/ahmadateya/flotta-edge-example-workload:latest
```

### GitHub Repository
- [https://github.com/ahmadateya/flotta-edge-example](https://github.com/ahmadateya/flotta-edge-example)
