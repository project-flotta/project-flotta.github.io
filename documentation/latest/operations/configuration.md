---
layout: documentation
---

# Operator Config

## Deploying workloads

Workload can be deployed to devices **after** they are registered with the
cluster. `EdgeWorkload` can be deployed only on edge devices in the same
namespace.

### Deploying by device ID

---
**Note**

When both methods are used in one `EdgeWorkload`, this one takes precedence over the selector-based one.

---

`EdgeWorkload` can be deployed on one chosen device by specifying its name in `spec.device` property.

For example, for `EdgeDevice` `242e48d0-286b-4170-9b97-95502066e6ae`, following property should be set in `EdgeWorkload` yaml:

```yaml
spec:
  ...
  device: 242e48d0-286b-4170-9b97-95502066e6ae
  ...
```

### Deploying with selector

`EdgeWorkload` can be installed on multiple devices using label selectors.

To deploy your workload using this method:

1) Label chosen `EdgeDevice` objects;

 For example:

 `oc label edgedevice 242e48d0-286b-4170-9b97-95502066e6ae dc=emea`

2) Select `dc=emea` label in the `EdgeWorkload` specification:

```yaml
spec:
 deviceSelector:
   matchLabels:
     dc: emea
```
   or
```yaml
spec:
 deviceSelector:
   matchExpressions:
     - key: dc
       operator: In
       values: [emea]
```

The second approach can be used for matching multiple values of one label. For example:
```yaml
spec:
 deviceSelector:
   matchExpressions:
     - key: dc
       operator: In
       values: [emea, apac]
```

3) Create the `EdgeWorkload` in the cluster:

```shell
kubectl apply -f your-workload.yaml
```

### Inspecting workload status

To check statuses of all workloads deployed to an edge device:

```shell
kubectl get edgedevice <edge device name> -ojsonpath="{range .status.workloads[*]}{.name}{':\t'}{.phase}{'\n'}{end}"
```

To list all devices having chosen workload deployed:

```shell
oc get edgedevice -l workload/<workload-name>="true"
```

`EdgeDevice` is labeled with `workload/<workload-name>="true"` when `EdgeWorkload` is added to it.

## Container Image Registries Credentials

Container images used by `EdgeWorkloads` may be hosted in private, protected
repositories requiring clients to present correct credentials. Users can provide
said credentials to Flotta operator as a `Secret` referred to by an
`EdgeWorkload`.

Secret should contain correct docker auth file under the `.dockerconfigjson` key:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: pull-secret
type: kubernetes.io/dockerconfigjson
data:
  .dockerconfigjson: ewoJImF1dGhzIjogewoJCSJxdWF5LmlvIjogewoJCQkiYXV0aCI6ICJabTl2SUdKaGNpQm1iMjhnWW1GeUNnPT0iCgkJfQoJfQp9Cg==
```

where `.dockerconfigjson` is a base64 encoded Docker auth file JSON:

```json
{
  "auths": {
    "quay.io": {
      "auth": "Zm9vIGJhciBmb28gYmFyCg=="
    }
  }
}
```

The above JSON can be taken from file created by running `podman login`, `docker
login` or similar.

Secret created above must be placed in the same namespace as `EdgeWorkload`
using it.

Reference to the above `Secret` in an `EdgeWorkload` spec:
```yaml
spec:
  imageRegistries:
    secretRef:
      name: pull-secret
```


## Logging

To change the verbosity of the logger, the user can update the value of the `LOG_LEVEL` field.
Admitted values are: 	`debug`, `info`, `warn`, `error`, `dpanic`, `panic`, and `fatal`.
Refer to [zapcore docs](https://github.com/uber-go/zap/blob/v1.15.0/zapcore/level.go#L32) for details on each log level.

For example:

```bash
kubectl patch cm -n flotta flotta-operator-manager-config \
  --type merge \
  --patch '{"data":{"LOG_LEVEL": "debug"}}'
```

In case of:
-  _Inside the cluster_ run, the pod will be automatically restarted.
-  _Outside the cluster_ run, the user must set the `LOG_LEVEL` field and manually restart the operator.


# Device 
