---
layout: documentation
---

# Operator Deployment options

Operator has different deployment modes, where some parameters can be turned
on/off based on a configMap value. To edit one of these parameters, the
following configmap should be editted. 

```shell
kubectl edit cm -n flotta flotta-manager-config
```

After any change in that file, flotta-operator and API need to be rebooted. 

### AUTO_APPROVAL_PROCESS

- **Default**: true 
- **Values**: _boolean_
- **Description**: If set to true, when a new device request to enrol, operator
automatically creates a device on the default namespace. Using this way there is
no need to have human interaction to start running workloads on any device.

### EDGEWORKLOAD_CONCURRENCY

- **Default**: 5
- **Values**: _integer_
- **Description**: Number of concurrent goroutines to create for handling
  EdgeWorkload reconcile

### ENABLE_WEBHOOKS

- **Default**: true
- **Values**: _boolean_
- **Description**: If Webhooks are enabled, an admission webhook is created and
  checked when any user submits any change to any project-flotta.io CRD.

### LEADER_ELECT
- **Default**: false
- **Values**: _boolean_
- **Description**: Enable leader election for controller manager. Enabling this
  will ensure there is only one active controller manager.

### LOG_LEVEL

- **Default**: info
- **Values**: [debug, info, warn, error, dpanic, panic, fatal]
- **Description**:  Log level for operator, by default is info and change in the
  configmap will automatically reload the config.

### MAX_CONCURRENT_RECONCILES

- **Default**: 3
- **Values**: __positive integer__
- **Description**: MaxConcurrentReconciles is the maximum number of concurrent
  Reconciles which can be run

### METRICS_ADDR

- **Default**: :8080
- **Values**: __port range__
- **Description**: Where operator/API will expose prometheus metrics.

### OBC_AUTO_CREATE

- **Default**: false
- **Values**: __boolean__
- **Description**: Enable OBC auto creation when EdgeDevice is registered

### PROBE_ADDR

- **Default**: :8081
- **Values**: __port range__
- **Description**: The address the probe endpoint binds to.

### WEBHOOK_PORT

- **Default**: :9443
- **Values**: __port range__
- **Description**: WebhookPort is the port that the webhook server serves at.
