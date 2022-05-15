---
layout: documentation
title: Manual installation
---
## Base repos to use

These are the base repos that project-flotta needs to run as expected:

|Dependecy             | Repo                                           | Git Version                                         |
|----------------------|------------------------------------------------|-----------------------------------------------------|
|flotta-operator       | [project-flotta/flotta-operator][operator]     | main                                                |
|flotta-device-worker  | [project-flotta/flotta-device-worker][device]  | main                                                |
|yggdrasil             | [RedHatInsights/yggdrasil][yggdrasil]          | main(since d69d38da3de3c0a473cd0bd6a713e72c2ea842f9)|
{: .table }

[operator]: https://github.com/project-flotta/flotta-operator
[device]: https://github.com/project-flotta/flotta-device-worker
[yggdrasil]: https://github.com/RedHatInsights/yggdrasil

## Common things to all repos:

### Makefiles

By default, project use Makefiles, and all the project has a help
section where information can be obtained:

This is the example when running make help in the flotta-operator repo.

```shell
$ -> make help

Usage:
  make <target>

General
  help             Display this help.

Development
  manifests        Generate WebhookConfiguration, ClusterRole and CustomResourceDefinition objects.
  generate         Generate code containing DeepCopy, DeepCopyInto, and DeepCopyObject method implementations.
  fmt              Run go fmt against code.
  vet              Run go vet against code.
  gosec            Run gosec locally
  imports          fix and format go imports
  lint             Check if the go code is properly written, rules are in .golangci.yml
  test             Run tests.
  test             Run tests.

Build
  build            Build manager binary.
  fast-build       Fast build manager binary for local dev.
  run              Run a controller from your host.
  docker-build     Build docker image with the manager.
  docker-push      Push docker image with the manager.

Deployment
  install          Install CRDs into the K8s cluster specified in ~/.kube/config.
  uninstall        Uninstall CRDs from the K8s cluster specified in ~/.kube/config.
  deploy           Deploy controller to the K8s cluster specified in ~/.kube/config.
  undeploy         Undeploy controller from the K8s cluster specified in ~/.kube/config.
  gen-manifests    Generates manifests for deploying the operator into $(TARGET)-flotta-operator.yaml
  install-router   Install openshift router
  controller-gen   Download controller-gen locally if necessary.
  kustomize        Download kustomize locally if necessary.
  ginkgo           Download ginkgo locally if necessary.
  client-gen       Download client-gen locally if necessary.
  lister-gen       Download lister-gen locally if necessary.
  informer-gen     Download client-gen locally if necessary.
  k8s-client-gen   Generate typed client for flotta project.
  validate-swagger  Validate swagger
$ ->
```


## Operator installation

For running operator, you need to install the CRD first, the best way to develop
is in a small Kubernetes cluster, like Kind or Minikube.

To install Operator you need to think that there are two main parts, the CRD
installation and the operator itself.

To install CRD, you need to run the following:

```
$ -> make install
/home/eloy/dev/upstream/project-flotta/k4e-operator/bin/kustomize build config/crd | kubectl apply -f -
customresourcedefinition.apiextensions.k8s.io/edgeconfigs.management.project-flotta.io configured
customresourcedefinition.apiextensions.k8s.io/edgedevices.management.project-flotta.io configured
customresourcedefinition.apiextensions.k8s.io/edgedevicesets.management.project-flotta.io configured
customresourcedefinition.apiextensions.k8s.io/edgedevicesignedrequest.management.project-flotta.io configured
customresourcedefinition.apiextensions.k8s.io/edgeworkloads.management.project-flotta.io configured
customresourcedefinition.apiextensions.k8s.io/playbookexecutions.management.project-flotta.io configured
```

To run the operator, some dependencies need to be executed first, like
openshift-router and cert-manager:

```shell
make install-router
make install-cert-manager
```

To run operator locally, you can use the following code:

```shell
make run
```

For registering devices, it's important to download certs and set correct
permission:

```shell
$ -> sudo rm /tmp/*.pem
$ -> make get-certs
kubectl get secret -n flotta flotta-ca  -o json | jq '.data."ca.crt"| @base64d' -r >/tmp/ca.pem
kubectl -n flotta get secret reg-client-ca-jnpmz68qfr -o json | jq -r '.data."client.crt"| @base64d' > /tmp/cert.pem
kubectl -n flotta get secret reg-client-ca-jnpmz68qfr -o json | jq -r '.data."client.key"| @base64d' > /tmp/key.pem
$ -> sudo chown root:root /tmp/*.pem
```

## Device installation

On device, we have two different things to install, yggdrasil and device worker.
There are two ways to run this piece:

> ⚠️ **Golang 1.16**: By default, device needs to compile in Golang 1.16 mainly
> because this software needs to be packaged as RPM, so the version for
> RHEL8/Fedora 35 is golang 1.16

### Single way with Yggdrasil:

This way, means that Yggdrasil already knows where the device-worker is located,
and it's defined on workers.toml.

So for this, on device-worker repo the following command should be run:

```shell
sudo make install
```

This will create two files:

```shell
$ -> cat /usr/local/etc/yggdrasil/workers/device-worker.toml
exec = "/usr/local/libexec/yggdrasil/device-worker"
protocol = "grpc"
env = []
$ -> ls /usr/local/libexec/yggdrasil/device-worker
/usr/local/libexec/yggdrasil/device-worker
```

And yggdrasil can run with the following command:

```shell
sudo ./yggd \
  --log-level trace \
  --protocol http\
  --path-prefix api/flotta-management/v1\
  --client-id $(cat /etc/machine-id)\
  --cert-file /tmp/cert.pem\
  --key-file /tmp/key.pem\
  --ca-root /tmp/ca.pem\
  --server 127.0.0.1:8043
```

That you can see that device-worker is running and starting to get data from
Flotta Edge API:

```
[yggd] 2022/05/10 15:55:52 /home/eloy/dev/upstream/project-flotta/yggdrasil/cmd/yggd/main.go:201: starting yggd version 0.2.98
....
[yggd] 2022/05/10 15:55:52 /home/eloy/dev/upstream/project-flotta/yggdrasil/cmd/yggd/main.go:377: starting worker: device-worker
...
[yggd] 2022/05/10 15:55:52 /home/eloy/dev/upstream/project-flotta/yggdrasil/cmd/yggd/worker.go:114: /usr/local/libexec/yggdrasil/device-worker: Data directory: /usr/local/etc/yggdrasil/device
[yggd] 2022/05/10 15:55:52 /home/eloy/dev/upstream/project-flotta/yggdrasil/cmd/yggd/worker.go:114: /usr/local/libexec/yggdrasil/device-worker: device config file: /usr/local/etc/yggdrasil/device/device-config.json
```

Running device-worker managed by yggdrasil is how the end users run in their
devices, so this is the closest way to replicate user issues.

### Separate instance for yggdrasil and device-worker

Because separate services are useful when developing, this way is useful to be
able to separate logs from yggdrasil and device-worker, and be able to focus
only on the device-worker part:

Run yggdrasil in one tab, with the following unixsocket `@yggd`

```shell
sudo ./yggd \
  --log-level trace \
  --protocol http\
  --path-prefix api/flotta-management/v1\
  --client-id $(cat /etc/machine-id)\
  --cert-file /tmp/cert.pem\
  --key-file /tmp/key.pem\
  --ca-root /tmp/ca.pem\
  --socket-addr @yggd\
  --server 127.0.0.1:8043
```

And in other tab, just start device-worker manually, and making sure that
`/usr/local/etc/yggdrasil/workers/device-worker.toml` is not present at all.

```
sudo YGG_LOG_LEVEL=debug \
    YGG_CONFIG_DIR="/tmp/device" \
    YGG_SOCKET_ADDR="unix:@yggd"
    YGG_CLIENT_ID="$(cat /etc/machine-id)"\
    go run cmd/device-worker/main.go
```

And now, device-worker will register to the API, and start to do all
enrolment/registration phase.
