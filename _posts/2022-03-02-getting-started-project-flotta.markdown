---
layout: post
title:  "Getting started with Flotta Operator Part 1"
date:   2022-02-03 11:44:17 -0400
categories: flotta
author: Ondra Machacek
tags:
  - guide
  - flotta
  
summary-1: Getting started guide with Flotta
---
In this blog post series we would like to show you how to get started with the _Flotta_ project.
The _Flotta_ operator is the Kubernetes operator used to manage the workloads of the edge devices via
Kubernetes API. In order to manage the edgedevices and workloads you need to have Kubernetes or OpenShift up and
running. Unfortunately the _Flotta_ operator is not yet published on the operator hub, so we have to deploy it manually from the github repo.

### Install Prerequisites for Flotta Operator
Following are the prerequisites:

```bash
 - Kubernetes or OpenShift cluster running with kubectl configured
 - Cert manager
 - OpenShift route
 - Noobaa (optional)
```

_Flotta_ requires the [cert manager](https://cert-manager.io/docs/) for TLS key management for webhooks, so if you don't have it up and running on your cluster,
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
registration time. By default, [_Object Bucket Claim_](https://github.com/kube-object-storage/lib-bucket-provisioner/blob/master/doc/design/object-bucket-lib.md#design) (OBC) auto-creation is disabled. To enable it, follow the instructions [below](#enable-object-bucket-claim-auto-creation).
To use _Noobaa_ to create a bucket claim for each device on registration you must enable OBC auto-creation.

For Installing [Noobaa](https://noobaa.github.io/) on the cluster, follow _Noobaa_'s [installation guide](https://github.com/noobaa/noobaa-operator#usage).
Note that _Noobaa_ requires additional resources, therefore additional memory and CPU are needed (+2 cpu, +5Gi memory).
_Noobaa_ also requires a local storage class and a default storage class to be present on the cluster.

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

By default, the _Flotta_ operator is deployed in `flotta` namespace.

```bash
$ kubectl get all -n flotta
NAME                                             READY   STATUS    RESTARTS        AGE
pod/flotta-controller-manager-7fd45874c6-wxxfv   2/2     Running   0               3d17h
pod/flotta-edge-api-8649fbb9dc-bt4r9             2/2     Running   0               3d17h

NAME                                                TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/flotta-controller-manager-metrics-service   ClusterIP   10.128.238.94    <none>        8443/TCP,8080/TCP            3d17h
service/flotta-edge-api                             ClusterIP   10.129.85.18     <none>        8043/TCP,8080/TCP,8443/TCP   3d17h
service/flotta-webhook-service                      ClusterIP   10.128.120.232   <none>        443/TCP                      3d17h

NAME                                        READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/flotta-controller-manager   1/1     1            1           3d17h
deployment.apps/flotta-edge-api             1/1     1            1           3d17h

NAME                                                   DESIRED   CURRENT   READY   AGE
replicaset.apps/flotta-controller-manager-7fd45874c6   1         1         1       3d17h
replicaset.apps/flotta-edge-api-8649fbb9dc             1         1         1       3d17h

NAME                                       HOST/PORT           PATH   SERVICES          PORT    TERMINATION   WILDCARD
route.route.openshift.io/flotta-edge-api   project-flotta.io          flotta-edge-api   yggds   passthrough   None

```

_Flotta_ operator deploys two [CustomResourceDefinitions (CRDs)](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/#customresourcedefinitions):
1. [EdgeWorkloads](https://github.com/project-flotta/flotta-operator/blob/main/config/crd/bases/management.project-flotta.io_edgeworkloads.yaml), used to manage the workloads.
2. [EdgeDevices](https://github.com/project-flotta/flotta-operator/blob/main/config/crd/bases/management.project-flotta.io_edgedevices.yaml) used to manage the devices.
3. [EdgeDeviceSet](https://github.com/project-flotta/flotta-operator/blob/main/config/crd/bases/management.project-flotta.io_edgedevicesets.yaml) used to manage set of devices.
4. [EdgeDeviceSignedRequest](https://github.com/project-flotta/flotta-operator/blob/main/config/crd/bases/management.project-flotta.io_edgedevicesignedrequest.yaml) used to manage approval of devices.

```bash
$ kubectl get crd | grep project-flotta.io
edgedevices.management.project-flotta.io               2022-05-15T13:25:11Z
edgedevicesets.management.project-flotta.io            2022-05-15T13:25:11Z
edgedevicesignedrequest.management.project-flotta.io   2022-05-15T13:25:11Z
edgeworkloads.management.project-flotta.io             2022-05-15T13:25:11Z
```

By default, both operator manifests (for _OCP_ and _k8s_) assume [ObjectBucketClaim CRD](https://github.com/kube-object-storage/lib-bucket-provisioner/blob/master/pkg/apis/objectbucket.io/v1alpha1/objectbucketclaim_types.go) is installed on the cluster.
If it is not installed, there are two options, based on the needs:

#### Enable Object Bucket Claim Auto Creation
To enable _ObjectBucketClaim_ auto-creation, Flotta's operator config map needs to be patched and Flotta's operator needs to be restarted:
```bash
kubectl patch cm -n flotta flotta-manager-config --type merge --patch '{ "data": { "OBC_AUTO_CREATE": "true"} }'
kubectl rollout restart deploy/flotta-controller-manager -n flotta
```

That's it for the operator side, next time we will take a look how to provision a machine with edge device, where we will deploy a simple nginx workload.
