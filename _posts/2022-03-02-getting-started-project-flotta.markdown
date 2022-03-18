---
layout: post
title:  "Getting started with Flotta Operator Part 1"
date:   2022-02-03 11:44:17 -0400
categories: flotta
author: Ondra Machacek
tags:
  - guide
  - flotta
  
summary-1: Getting started guide with flotta
---
In this blog post series we would like to show you how to get started with the `flotta` project.
The `flotta` operator is the Kubernetes operator used to manage the workloads of the edge devices via
Kubernetes API. In order to manage the edgedevices and workloads you need to have Kubernetes or OpenShift up and
running. Unfortunatelly the `flotta` operator is not yet published on the operator hub, so we have to deploy it manually from the github repo.

Following are the prerequisites:

```bash
 - Kubernetes or OpenShift cluster running with kubectl configured
 - Cert manager
```

`Flotta` requires the [cert manager](https://cert-manager.io/docs/) for TLS key management for webhooks, so if you don't have it up and running on your cluster,
you can execute following command to install it:

```bash
$ kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.7.1/cert-manager.yaml
$ kubectl wait --for=condition=Ready pods --all -n cert-manager --timeout=60s
```

To deploy the latest version of the `flotta` operator execute following command:

For OpenShift Container Platform (OCP):
```bash
$ kubectl apply -f https://github.com/project-flotta/flotta-operator/releases/download/v0.0.1/ocp-flotta-operator.yaml
```
For kubernetes:
```bash
$ kubectl apply -f https://github.com/project-flotta/flotta-operator/releases/download/v0.0.1/k8s-flotta-operator.yaml
```

The only difference between the two files is in how [OCP and Kubernetes](https://cloud.redhat.com/blog/kubernetes-ingress-vs-openshift-route) enable external access to services.

Kubernetes uses the `Ingress` object to signal the Kubernetes platform that a certain service needs to be accessible to the outside world and it contains the configuration needed.
OCP uses the `Route`, that is equivalent to `Ingress` with additional capabilities.

By default the `flotta` operator is deployed in `flotta` namespace.

```bash
$ kubectl get all -n flotta
NAME                                                     READY   STATUS    RESTARTS   AGE
pod/flotta-operator-controller-manager-b7758f7b8-gww7d   2/2     Running   0          18h

NAME                                                         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)             AGE
service/flotta-operator-controller-manager                   ClusterIP   10.103.155.185   <none>        8888/TCP,8043/TCP   18h
service/flotta-operator-controller-manager-metrics-service   ClusterIP   10.98.35.222     <none>        8443/TCP,8080/TCP   18h
service/flotta-operator-webhook-service                      ClusterIP   10.96.199.135    <none>        443/TCP             18h

NAME                                                 READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/flotta-operator-controller-manager   1/1     1            1           18h

NAME                                                           DESIRED   CURRENT   READY   AGE
replicaset.apps/flotta-operator-controller-manager-b7758f7b8   1         1         1       18h
```

`Flotta` operator deploys two [CustomResourceDefinitions (CRDs)](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/#customresourcedefinitions):
1. [edgedeployments](https://github.com/project-flotta/flotta-operator/blob/main/config/crd/bases/management.project-flotta.io_edgedeployments.yaml), used to manage the workloads.
2. [edgedevices](https://github.com/project-flotta/flotta-operator/blob/main/config/crd/bases/management.project-flotta.io_edgedevices.yaml) used to manage the devices.

```bash
$ kubectl get crd | grep project-flotta.io
edgedeployments.management.project-flotta.io   2022-03-01T14:07:17Z
edgedevices.management.project-flotta.io       2022-03-01T14:07:17Z
```

That's it for the operator side, next time we will take a look how to provision a machine with edgedevice, where we will deploy a simple nginx workload.
