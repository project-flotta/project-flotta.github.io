---
layout: post
title:  "Writing metrics to control plane"
date:   2022-04-11 14:00:00 +0300
categories: flotta
author: Yaron Dayagi
tags:
  - guide
  - flotta
  
summary-1: Writing metrics to control plane
---

Flotta edge devices collect metrics from device's system and workloads. These metrics are stored locally in the device. How do we get the metrics to the control plane? How can we view the metrics in control plane? These questions are what this blog post is about.

## Device metrics - quick overview

Configuring a device to collect metrics is covered by the [device-metrics user guide](https://github.com/project-flotta/flotta-operator/blob/main/docs/user-guide/device-metrics.md). Flotta agent in the device scrapes system and workloads metrics and writes to a local TSDB folder. For system metrics we use `node_exporter`. Thanks to that you can see metrics such as `node_memory_MemAvailable_bytes`. The local TSDB enforces a retention policy.

##  Prometheus Remote Write API

[Prometheus Remote Write API](https://prometheus.io/docs/prometheus/latest/configuration/configuration/#remote_write) is an HTTP API that allows a client to write metrics to a remote server (a.k.a. receiver). The [Prometheus Integrations page](https://prometheus.io/docs/operating/integrations/#remote-endpoints-and-storage) lists various servers that implement the server side of Remote Write API. Flotta project includes an example for using [Thanos](https://thanos.io/tip/components/receive.md/#receiver) as a receiver.

## Flotta project's solution

Flotta's solution is to use the Prometheus Remote Write API for writing to a server in the control plane. Flotta agent, periodically reads from the local TSDB (5 minutes) and writes to a receiver in the control plane. The client in the agent is a reuse of [Prometheus Write Client](https://github.com/prometheus/prometheus/tree/main/storage/remote).
Configuring the agent is explained [here](https://github.com/project-flotta/flotta-operator/blob/main/docs/user-guide/device-metrics.md). The most important part is the URL for accessing the receiver from the device. It can be either HTTP or HTTPS.
The configuration allows you to adjust the request size sent to the server and the timeout of the connection to the server.

What happens if device can not connect to receiver for a few days? The agent saves the timestamp of the last written metric. It will start writing from that point in time until all the metrics in the TSDB are written. Metrics that were deleted by TSDB retention before having a chance to send them are lost.

What happens to sent metrics? Saving the timestamp of last written metric avoids writing same metrics again. But who deletes these metrics? TSDB retention.

## Example of Thanos receiver

The [Device Metrics user guide](https://github.com/project-flotta/flotta-operator/blob/main/docs/user-guide/device-metrics.md) includes an example of a Thanos deployment in K8S. The example includes two deployments one with TLS and one without. The deployment has two servers (containers). One is the receiver. Another is the querier. Querier is used for reading the metrics that the receiver saved. Thanos supports PromQL so you can use it in Grafana. The querier has two address configurations. One, is the connection to the receiver. Another, is the HTTP address to listen for queries. The receiver also has two address configurations. One, is the server address for accepting connections from querier. Another, is the HTTP address that listens from remote writes.
