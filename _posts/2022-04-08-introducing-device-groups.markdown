---
layout: post
title:  "Introduction to edge device groups"
date:   2022-04-08 12:00:00 +0100
categories: flotta
author: Jakub Dżon
tags:
  - guide
  - flotta
  
summary-1: Introduction to edge device groups
---

If you are Flotta user that needs to manage large numbers of devices and doesn't want to change configuration of each 
of them separately, using Edge Device Groups is the perfect approach. With the use of Edge Device Groups you can change 
configuration of any number of device by changing only one CR - `EdgeDeviceGroup` and this blog post will show you how.

### EdgeDeviceGroup configuration

User may define the same configuration elements using `EdgeDeviceGroup` as one would with `EdgeDevice` and configuration 
defined in the `EdgeDeviceGroup` would be applied to all edge devices using it. `EdgeDeviceGroup`  **always** takes 
precedence over whatever is defined in the `EdgeDevice` as a whole. It means that even if some element is not present in 
the `EdgeDeviceGroup`, usual default values are used for it, even if it is defined at the level of `EdgeDevice`.

If corresponding `EdgeDeviceGroup` cannot be found, `EdgeDevice` configuration is used.

Configuration that can be defined with `EdgeDeviceGroup`:
- heartbeat (`spec.heartbeat`);
- metrics (`spec.metrics`);
- data transfer (`spec.storage`);
- log collection (`spec.logCollection`);
- OS configuration (`spec.osInformation`).

Full `EdgeDeviceGroup` CR might look as follows:

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDeviceGroup
metadata:
  name: sample-group
spec:
  heartbeat:
    periodSeconds: 5 # Interval in seconds with which the heartbeat messages should be sent from the agent 
    hardwareProfile: # Defines the scope of hardware information sent with the heartbeat messages; currently unused
      include: true # Specifies whether the hardware should be sent at all
      scope: full # Specifies how much information should be provided; "full" - everything; "delta" - only changes compared to the previous updated
  metrics:
    retention:
      maxMiB: 200 # Specifies how much disk space should be used for storing persisted metrics on the device
      maxHours: 24 # Specifies how long should persisted metrics be stored on the device disk
    system:
      interval: 60 # Interval in seconds with which the device system metrics should be collected
      allowList:
        name: allow-list-map # Defines name of a ConfigMap containing list of system metrics that should be scraped
        disabled: true #  When set to true instructs the device to turn off system metrics collection
  osInformation:
    automaticallyUpgrade: true # Flag defining whether OS upgrade should be performed automatically when the commitID changes
    commitID: 0305686e69d673cb15ad459990fab4a3e4c5aba1 # Commit ID of desired OS ostree version for the device
    hostedObjectsURL: http://images.project-flotta.io # URL of the hosted commits web server
  storage:
    s3:
      secretName: common-s3-secret # Name of the secret containing S3 API access credentials
      configMapName: common-s3-config #Name of a config map containing S3 API access configuration options
      createOBC: false # Flag defining whether the OBC should be automatically created for the device (if this feature is disabled for the operator)
  logCollection:
    syslog:
      kind: syslog # Kind of a log collection system. Currently, only `syslog` is available
      bufferSize: 12 # Size of a log sending buffer in kilobytes
      syslogConfig: 
        name: syslog-config-map # Name of a config map containing syslog connection configuration
```

To make specific `EdgeDevice` use specific `EdgeDeviceGroup` configuration, user needs to add
`flotta/member-of: <edge device group name>` label to the `EdgeDevice`.
For example, if there is a `group-1` `EdgeDeviceGroup` and `device-1` `EdgeDevice`, user needs to issue following
command to build the relationship between them:
```shell
kubectl label edgedevice device-1 flotta/member-of=group-1
```

### Managing multiple devices configuration
Let's have a look how `EdgeDeviceGroups` can be used in practice - let's register three different edge devices 
(`device-1`, `device-2`, `device-3`), create two edge device groups (`group-1` and `group-2`) and then assign devices 
to chosen groups. To illustrate how the configuration defined in the `EdgeDeviceGroup` influences device configuration, 
two of the devices will have different initial configuration.

#### Preparations
Our starting point is three edge devices registered with our cluster:
```shell
$kubectl get edgedevice
NAME       AGE
device-1   13s
device-2   22s
device-3   51s
```

Let's configure `device-1` heartbeat interval to 15 seconds:
```shell
kubectl patch edgedevice device-1 --type merge -p '{"spec":{"heartbeat": {"periodSeconds": 15}}}'
```

which will result in on-device configuration file (`/etc/yggdrasil/device/device-config.json`) to look like this:
```json
{
 "configuration": {
  "heartbeat": {
   "hardware_profile": {},
   "period_seconds": 15
  },
  "metrics": {
   "receiver": {
    "request_num_samples": 30000,
    "timeout_seconds": 10
   }
  }
 },
 "device_id": "device-1",
 "version": "54429"
}
```

Be aware that `metrics` settings are set to default values, not explicitly set in the `EdgeDevice` CR.

Next let's configure `device-2` to have system metrics collection disabled:
```shell
kubectl patch edgedevice device-2 --type merge -p '{"spec":{"metrics": {"system": {"disabled": true}}}}'
```

which will cause the on-device to be set to:
```json
{
 "configuration": {
  "heartbeat": {
   "hardware_profile": {},
   "period_seconds": 60
  },
  "metrics": {
   "receiver": {
    "request_num_samples": 30000,
    "timeout_seconds": 10
   },
   "system": {
    "disabled": true,
    "interval": 60
   }
  }
 },
 "device_id": "device-2",
 "version": "54651"
}
```

In this case `metrics.receiver` and `heartbeat` settings are set to default values.

The `device-3` will remain unchanged and use default values:
```json
{
 "configuration": {
  "heartbeat": {
   "hardware_profile": {},
   "period_seconds": 60
  },
  "metrics": {
   "receiver": {
    "request_num_samples": 30000,
    "timeout_seconds": 10
   }
  }
 },
 "device_id": "device-3",
 "version": "54249"
}
```

#### EdgeDeviceGroup creation
Let's create two edge device groups, that will be later used by the devices above:

```shell
kubectl apply -f -<<EOF
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDeviceGroup
metadata:
  name: group-1
spec:
  heartbeat:
    periodSeconds: 5
  metrics:
    system:
      interval: 600
  osInformation:
    automaticallyUpgrade: true
EOF
```

```shell
kubectl apply -f -<<EOF
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDeviceGroup
metadata:
  name: group-2
spec:
  heartbeat:
    periodSeconds: 5
  metrics:
    system:
      interval: 1200
  osInformation:
    automaticallyUpgrade: false
EOF
```

#### EdgeDeviceGroup membership
Creation of the groups doesn't change the configuration of the existing edge devices yet. To make the devices use the 
group-level configuration, the devices need to be labelled:

Assignment of `device-1` `EdgeDevice` to `group-1` `EdgeDeviceGroup`:
```shell
kubectl label edgedevice device-1 flotta/member-of=group-1
```

Assignment of `device-3` `EdgeDevice` to `group-1` `EdgeDeviceGroup`:
```shell
kubectl label edgedevice device-3 flotta/member-of=group-1
```

After issuing the above commands, the on-device configuration of both `device-1` and `device-3` are group-driven and are 
exactly the same:

`device-1`:
```json
{
  "configuration": {
    "heartbeat": {
      "hardware_profile": {},
      "period_seconds": 5
    },
    "metrics": {
      "receiver": {
        "request_num_samples": 30000,
        "timeout_seconds": 10
      },
      "system": {
        "interval": 600
      }
    },
    "os": {
      "automatically_upgrade": true
    }
  },
  "device_id": "device-1",
  "version": "55501"
}
```

`device-3`:
```json
{
  "configuration": {
    "heartbeat": {
      "hardware_profile": {},
      "period_seconds": 5
    },
    "metrics": {
      "receiver": {
        "request_num_samples": 30000,
        "timeout_seconds": 10
      },
      "system": {
        "interval": 600
      }
    },
    "os": {
      "automatically_upgrade": true
    }
  },
  "device_id": "device-3",
  "version": "55497"
}
```

Assigning `device-2` to `group-2`:
```shell
kubectl label edgedevice device-2 flotta/member-of=group-2
```

results in following configuration being changed on the device to:
```json
{
 "configuration": {
  "heartbeat": {
   "hardware_profile": {},
   "period_seconds": 5
  },
  "metrics": {
   "receiver": {
    "request_num_samples": 30000,
    "timeout_seconds": 10
   },
   "system": {
    "interval": 1200
   }
  },
  "os": {}
 },
 "device_id": "device-2",
 "version": "55941"
}
```

Now increasing the heartbeat frequency of `device-1` and `device-3` to 10 minutes at one time is as easy as patching `group-1`:
```shell
kubectl patch edgedevicegroup group-1 --type merge -p '{"spec":{"heartbeat": {"periodSeconds": 600}}}'
```

the on-device configuration on both `device-1` and `device-3` will show the above change:

`device-1`:
```json
{
 "configuration": {
  "heartbeat": {
   "hardware_profile": {},
   "period_seconds": 600
  },
  "metrics": {
   "receiver": {
    "request_num_samples": 30000,
    "timeout_seconds": 10
   },
   "system": {
    "interval": 600
   }
  },
  "os": {
   "automatically_upgrade": true
  }
 },
 "device_id": "device-1",
 "version": "55507"
}
```

`device-3`:
```json
{
 "configuration": {
  "heartbeat": {
   "hardware_profile": {},
   "period_seconds": 600
  },
  "metrics": {
   "receiver": {
    "request_num_samples": 30000,
    "timeout_seconds": 10
   },
   "system": {
    "interval": 600
   }
  },
  "os": {
   "automatically_upgrade": true
  }
 },
 "device_id": "device-3",
 "version": "55505"
}
```

#### EdgeDeviceGroup removal
As mentioned earlier, removal of an `EdgeDeviceGroup` will result in devices switching to `EdgeDevice`-level defined settings.

Removal of the `group-2` `EdgeDeviceGroup`:
```shell
kubectl delete edgedevicegroup group-2
```

will cause `device-2` to use the configuration specified in its `EdgeDevice` CR:
```json
{
 "configuration": {
  "heartbeat": {
   "hardware_profile": {},
   "period_seconds": 60
  },
  "metrics": {
   "receiver": {
    "request_num_samples": 30000,
    "timeout_seconds": 10
   },
   "system": {
    "disabled": true,
    "interval": 60
   }
  }
 },
 "device_id": "device-2",
 "version": "55948"
}
```