---
layout: documentation
title: Developer guide
---


# Operator


## CI Jobs

- *Kind*: E2E test running on each PR, can be found on
  `.github/workflows/kind.yaml`
- *Go/build*: Build current code and checks that unittest are working
- *Go/Lint*: Check that code is correctlt linted
- *Go/YamlLint*: Check that Yaml files are correctlt linted
- *Go/SecurityScanner*: Checks that the current code is staticly checked by
  [gosec](https://github.com/securego/gosec)
- *Go/Test Coverage*: Report the unit test code coverage, fails if went down.

## Logging

Log configuration can be found [here](../operations/configuration.md)

[logr](https://github.com/go-logr/logr) is a logging API for Go. It provides a simple interface for logging under which there is an actual logger that implements the `logr` interface.

[Zap](https://github.com/uber-go/zap) is a log library that implements `logr` interface.

[SDK-generated operators](https://sdk.operatorframework.io/docs/building-operators/golang/references/logging/) use the logr interface to log. Operator SDK by default uses a [zap-based logger](https://pkg.go.dev/sigs.k8s.io/controller-runtime#section-readme) that is ready for production use. The default verbosity is set to `info` level.

_logr_ defines logger's verbosity levels numerically. To write log lines that are more verbose, `logr.Logger` has a [V()](https://pkg.go.dev/github.com/go-logr/logr#hdr-Verbosity) method. The higher the V-level of a log line, the less critical it is considered.
Level `V(0)` is the default, and `logger.V(0).Info()` has the same meaning as `logger.Info()`.

Levels in _logr_ correspond to [custom debug levels](https://pkg.go.dev/go.uber.org/zap/zapcore#Level) in _Zap_. Any given level in logr is represented by its inverse in zap (zapLevel = -1*logrLevel).
Thus, in _Zap_, higher levels are more important.

For example: _logr_ V(2) is equivalent to log level -2 in Zap, while _logr_ V(1) is equivalent to debug level -1 in _Zap_.

**To summarize:**

|Zap logging priority  | Zap enum     | logr                              |
|---------------------:| ------------ | --------------------------------- |
| -1                   | debug        | `.V(1).Info(...)`                 |
|  0                   | info         | `.V(0).Info(...)` or `.Info(...)` |
|  1                   | warn         | N.A.                              |
|  2                   | error        | `.Error(...)`                     |
|  3                   | dpanic       | N.A.                              |
|  4                   | panic        | N.A.                              |
|  5                   | fatal        | N.A.                              |

## E2E tests

### Prerequisites

 - k8s cluster or Openshift Cluster
 - Make sure that your `oc` or `kubectl` is configured properly to communicate with your cluster
 - Not needed for all test, OpenShift Cluster Storage or at least NooBaa.

### Running the tests

1.  Create container image of flotta operator.

```bash
# Build the flotta operator
$ make build

# Make sure you have configured k8s provider docker
# For example for minikube by running: eval $(minikube -p minikube docker-env)
# Then run the build of the container
$ IMG=flotta-operator:latest make docker-build

# Deploy the operator on k8s
$ make deploy IMG=flotta-operator

# Wait until the operator is ready
$ kubectl wait --timeout=120s --for=condition=Ready pods --all -n flotta
```

2.  Expose the flotta API

```bash
$ kubectl port-forward deploy/flotta-operator-controller-manager -n flotta --address 0.0.0.0 8043:8043 &
```

3.  Run the tests

```bash
$ make integration-test
```

### Troubleshooting

**kubectl wait timeouts:**

If timeout, debug the deployment logs by running:

```shell 
kubectl logs deploy/flotta-operator-controller-manager -n flotta
```

**Waiting for edge device timeouts in integration tests**:

Debug the edge device container by executing shell inside the container:

```shell
docker exec -it edgedevice1 journalctl -u yggdrasild.service
```

# Device Worker

## CI jobs
- *Go/build*: Build current code and checks that unittest are working
- *Go/Lint*: Check that code is correctlt linted
- *Go/SecurityScanner*: Checks that the current code is staticly checked by
  [gosec](https://github.com/securego/gosec)
