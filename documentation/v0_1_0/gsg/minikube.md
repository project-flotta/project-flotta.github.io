---
layout: documentation
title: Run flotta on minikube
---

Flotta can run on top of any Kubernetes distributions, for testing and
development you can follow this guide to get started running flotta on your
devices.

Let's start with minikube

```shell
---> minikube start
😄  minikube v1.22.0 on Fedora 35
🎉  minikube 1.25.2 is available! Download it: https://github.com/kubernetes/minikube/releases/tag/v1.25.2
💡  To disable this notice, run: 'minikube config set WantUpdateNotification false'

✨  Automatically selected the docker driver
👍  Starting control plane node minikube in cluster minikube
🚜  Pulling base image ...
🔥  Creating docker container (CPUs=2, Memory=3900MB) ...

🧯  Docker is nearly out of disk space, which may cause deployments to fail! (95% of capacity)
💡  Suggestion:

    Try one or more of the following to free up space on the device:

    1. Run "docker system prune" to remove unused Docker data (optionally with "-a")
    2. Increase the storage allocated to Docker for Desktop by clicking on:
    Docker icon > Preferences > Resources > Disk Image Size
    3. Run "minikube ssh -- docker system prune" if using the Docker container runtime
🍿  Related issue: https://github.com/kubernetes/minikube/issues/9024

🐳  Preparing Kubernetes v1.21.2 on Docker 20.10.7 ...
    ▪ Generating certificates and keys ...
    ▪ Booting up control plane ...
    ▪ Configuring RBAC rules ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

Check minikube status:

```shell
---> minikube status
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```


Flotta operator has a few tools that helps to install flotta, for that, let's
clone it:

```shell
git clone https://github.com/project-flotta/flotta-operator -b v0.1.0 --depth 1
cd flotta-operator
```

First, we need to install Openshift-router, the ingress that it's supported now:

```shell
---> make install-router
kubectl apply -f https://raw.githubusercontent.com/openshift/router/master/deploy/router_rbac.yaml
clusterrole.rbac.authorization.k8s.io/openshift-ingress-router created
clusterrolebinding.rbac.authorization.k8s.io/openshift-ingress-router created
clusterrolebinding.rbac.authorization.k8s.io/openshift-ingress-router-auth-delegator created
namespace/openshift-ingress created
serviceaccount/ingress-router created
kubectl apply -f https://raw.githubusercontent.com/openshift/router/master/deploy/route_crd.yaml
customresourcedefinition.apiextensions.k8s.io/routes.route.openshift.io created
kubectl apply -f https://raw.githubusercontent.com/openshift/router/master/deploy/router.yaml
deployment.apps/ingress-router created
kubectl wait --for=condition=Ready pods --all -n openshift-ingress --timeout=60s
pod/ingress-router-5b9b477c98-gx5pl condition met
```

Now let's install Flotta on the cluster:

```shell
make deploy IMG=quay.io/project-flotta/flotta-operator:v0.1.0 TARGET=k8s
```

A bunch of CRDs are now created, where the definitions can be found
[here](../operations/crd.md):

```
---> kubectl  api-resources | grep flotta
edgeconfigs                                    management.project-flotta.io/v1alpha1   true         EdgeConfig
edgedevices                                    management.project-flotta.io/v1alpha1   true         EdgeDevice
edgedevicesets                                 management.project-flotta.io/v1alpha1   true         EdgeDeviceSet
edgedevicesignedrequest           edsr         management.project-flotta.io/v1alpha1   true         EdgeDeviceSignedRequest
edgeworkloads                                  management.project-flotta.io/v1alpha1   true         EdgeWorkload
playbookexecutions                             management.project-flotta.io/v1alpha1   true         PlaybookExecution
--->
```

At the same time, in the flotta namespace an operator should be running:
```
---> kubectl -n flotta get pods
NAME                                                  READY   STATUS    RESTARTS   AGE
flotta-operator-controller-manager-5ffc74fd8c-wv9cm   2/2     Running   0          2m1s
--->
```

Flotta is now running and ready to register edgedevices. To register a
edgedevice we need first to retrieve the install scripts using the Makefile
target `agent-install-scripts`.

```
make agent-install-scripts
```

Now, two scripts are created:
  - hack/install-agent-dnf.sh: To install on normal Fedora installations
  - hack/install-agent-rpm-ostree.sh: To install on rpm-ostree devices.

Minikube is a local virtual machine, so `$ minikube ip` cannot be reached from
your edgedevice, for sharing the flotta API port to the edgedevice the best way
is to use kubectl port-forward:

```
$ kubectl port-forward service/flotta-operator-controller-manager -n flotta 8043 --address 0.0.0.0
```

On the device, with Fedora already installed, we need to execute the following:

```
$ sudo hack/install-agent-dnf.sh -i 192.168.2.10
```

Where 192.168.2.10 is your host ip.

After a while, if you list the devices in your cluster, you can see that the
edgedevice is already registered:

```
---> kubectl get edgedevices
NAME        AGE
camera-ny   118s
```

From here, you should be able to deploy workloads to these devices. As explained
[here](./running_workloads.md)
