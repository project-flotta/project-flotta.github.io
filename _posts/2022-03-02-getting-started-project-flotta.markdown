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
In this blog post series we would like to show you how to get started with the `Flotta` project.
The `Flotta` operator is the Kubernetes operator used to manage the workloads of the edge devices via
Kubernetes API. In order to manage the edgedevices and workloads you need to have Kubernetes or OpenShift up and
running. Unfortunately the `Flotta` operator is not yet published on the operator hub, so we have to deploy it manually from the github repo.

### Install Prerequisites for Flotta Operator
Following are the prerequisites:

```bash
 - Kubernetes or OpenShift cluster running with kubectl configured
 - Cert manager
 - OpenShift route
 - Noobaa (optional)
```

`Flotta` requires the [cert manager](https://cert-manager.io/docs/) for TLS key management for webhooks, so if you don't have it up and running on your cluster,
you can execute following command to install it:

```bash
$ kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.7.1/cert-manager.yaml
$ kubectl wait --for=condition=Ready pods --all -n cert-manager --timeout=60s
```

In addition, OpenShift router is needed for passing-through incoming TLS traffic into Flotta Edge API that handles incoming
requests from the edge devices.
For non-_OCP_ clusters types (_k8s_, _kind_, _minikube_), use the following command to install it:
```bash
$ kubectl apply -f https://raw.githubusercontent.com/openshift/router/master/deploy/router_rbac.yaml
$ kubectl apply -f https://raw.githubusercontent.com/openshift/router/master/deploy/route_crd.yaml
$ kubectl apply -f https://raw.githubusercontent.com/openshift/router/master/deploy/router.yaml
$ kubectl wait --for=condition=Ready pods --all -n openshift-ingress --timeout=60s
```

[Noobaa](https://noobaa.github.io/) is data service that provides S3 object-store interface. Flotta's Edge API enables
edge devices to send application data to S3 endpoint, into a bucket claim created automatically for each device at
registration time.

For Installing [Noobaa](https://noobaa.github.io/) on the cluster, follow _Noobaa_'s [installation guide](https://github.com/noobaa/noobaa-operator#usage).
Note that _Noobaa_ requires additional resources, therefore additional memory and CPU are needed (+2 cpu, +5Gi memory).
_Noobaa_ also requires a local storage class and a default storage class to be present on the cluster.

In order to skip the _Noobaa_ installation, follow the steps [below](2022-03-02-getting-started-project-flotta.markdown#disable-object-bucket-claim-auto-creation) to disable Object Bucket claim auto-creation.
 
### Install Flotta Operator
To deploy the latest version of the _Flotta_ operator execute following command:

For OpenShift Container Platform (_OCP_):
```bash
$ kubectl apply -f https://github.com/project-flotta/flotta-operator/releases/download/v0.1.0/ocp-flotta-operator.yaml
```
For kubernetes:
```bash
$ kubectl apply -f https://github.com/project-flotta/flotta-operator/releases/download/v0.1.0/k8s-flotta-operator.yaml
```

By default, the _flotta_ operator is deployed in `flotta` namespace.

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

By default, both operator manifests (for _OCP_ and _k8s_) assume [ObjectBucketClaim CRD](https://github.com/kube-object-storage/lib-bucket-provisioner/blob/master/pkg/apis/objectbucket.io/v1alpha1/objectbucketclaim_types.go) is installed on the cluster.
If it is not installed, there are two options, based on the needs:

#### Disable Object Bucket Claim Auto Creation
To disable _ObjectBucketClaim_ auto-creation, Flotta's operator config map needs to be patched and Flotta's operator needs to be restarted:
```bash
kubectl patch cm -n flotta flotta-operator-manager-config --type merge --patch '{ "data": { "OBC_AUTO_CREATE": "false"} }'
kubectl rollout restart deploy/flotta-operator-controller-manager -n flotta
```

That's it for the operator side, next time we will take a look how to provision a machine with edge device, where we will deploy a simple nginx workload.
