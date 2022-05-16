---
layout: documentation
title: Flotta concepts
---

The concepts chapter provides an overview of all aspects of Flotta. See the
getting started guides section if you are looking for an entry point
introduction to Flotta.

## Components overview

## Operator

The operator is responsible for handling all Custom Resources definitions from
project-flotta. All the resources that the operator manages can be found on CRD
spec or using the following command:

```shell
kubectl api-resources --api-group="management.project-flotta.io"
```

By default, all CRDs are created/updated or by the operator or by any Kubernetes
user. Edge devices are not capable of dealing with Kubernetes objects.

## Flotta Edge API

By default, all Edgedevices connect to the Flotta Edge API, where they can
retrieve the config and push information. This API is defined
[here](../operations/api.html)

Connectivity beetween the EdgeDevice to the API is using a Mutual TLS
connection, where we have two kinds of certificates.

- **Register certificate**: Is the certificate that the Edge Admin or factory
  admin injects for the first time in the edge device. This device can only make
  a registration Request to the Flotta Edge API.
- **User certificate**: Is the certificate that it's only valid for the specific
  device. This certificate uses a key that shouldn't leave the device, so the
  API signs the certificate with the User Pub Key. At the same time, the short
  lived cert, and Flotta operator managed to handle cert expiration.

Communication from Edgedevice to the API is like this:

{% mermaid %}
sequenceDiagram
autonumber
participant Agent as Device Agent
participant YGGD as Yggdrasil
participant API as Flotta Edge API

rect rgb(226, 232, 238)
  Agent ->> YGGD: Register (GRPC+Unixsocket)
  YGGD ->> Agent: 200 OK
  Agent ->> YGGD: Send with enrolment directive
  YGGD ->> API: Data message with enrolment directive
  API ->> YGGD: 208 OK device-exists
  YGGD ->> Agent: 208 OK device exists
  Agent ->> YGGD: Send with registration directive
  YGGD ->> API: Data message with registration directive
  API ->> YGGD: 200 OK with signed certificate
  YGGD ->> Agent: 200 OK with signed certificate.
  Note over YGGD, Agent: New client certificate writen
end

rect rgb(233, 237, 202)
  loop Heartbeat
    Agent -->> YGGD: Heartbeat
    YGGD-->> API: Heartbeat
    API -->> YGGD: 200 OK
    YGGD-->> Agent: 200 OK
  end
end
{% endmermaid %}

1. Flotta device-agent(Agent) register to Yggdrasil using Unixsocket and GRPC
   connection
2. Yggdrasil allows device-worker to register in the platform.
3. Agent needs to know if can enrol in the system, so for that send a enrolment
   directive.
4. Yggdrasil forward that message to the configured transport to the Flotta Edge API.
5. If device is already approved, Flotta Edge API will return back 208 status code to
   Yggdrasil.
6. Yggdrasil sends to the device agent the response.
7. Agent needs now to register to the API, and for that sends a data-message with
   the registration directive that includes a Certificate Signed Request(CSR).
8. Yggdrasil forward that message in the configured transport to the Flotta Edge API
9. If registration is successful, it will return a signed certificate based on
   the CSR
10. Yggdrasil sends to the agent the response. Agent rewrite the client certs to
   create new connections with the device certificates.
11. -14 Each minute, Agent sends heartbeat data to the operator, if the operator
returns 200 OK nothing happens, if returns 401 for the certificate expired the
registration process will be started again.

## EdgeDevice

An Edgedevice can be multiple things, from a tiny RPI Zero to a big X86 server.
For flotta, an Edgedevie is an Operating system where device-agent and Yggdrasil
are running, and some container workloads can be run by this daemon.

The communication from the edgedevice to the Kubernetes server is not required,
so all communication is to the Flotta Edge API. At the same time, there are
no things like CNI, CSI interfaces for getting it lightweight.

What project-flotta focused is that edgedevices can have one or multiple specs:

- Networks can be flaky, like a satellite, NB-IoT or Lorawan.
- Power consumption is a high priority; these devices can run on batteries.
- Devices can be turned off for a long period.
- Devices are insecure by default.
- Communication should always be encrypted.

The EdgeDevice is a CRD that it's defined [here](../operations/crd.html#edgedevice)

### Yggdrasil

Is a client daemon that establishes a receiving queue for instructions to be
sent to the system via a broker. For us, the broker is HTTP, and it’s the Flotta
Edge API.

### Device Agent

Device Agent is a worker for Yggdrasil, and it's the agent that deploys all
podman, systemd, logs for all workloads, and deals with the Commmunication to
the Flotta Edge API.

## EdgeDevice Signed Request

EdgeDevice Signed Request is a specific [CRD
type](../operations/crd.html#edgedevicesignedrequest). When AUTO_APPROVAL is set
to false, when device tries to register, but before it, and Edge Administrator
needs to approve where the device will land and what kind of configuration it'll
have.

## DeviceSets

When a platform has thousands of different devices, a configuration group is
needed to have similar configurations across different devices. A [Device
Set](../operations/crd.html#edgedeviceset) is one kind of CRD that allows users
to define this configuration.

Example:

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDeviceSet
metadata:
  name: set-1
spec:
  heartbeat:
    periodSeconds: 5
  metrics:
    system:
      interval: 600
  osInformation:
    automaticallyUpgrade: true
```

## EdgeWorkload

When a user wants to run a workload on a edgedevice, we use the [CRD
Edgeworkload](../operations/crd.html#edgeworkload). With this deployment option,
you can run containers on any edgedevice.

EdgeWorkload has the same configuration as the Pod Specification, plus some
other entries that are specific to Flotta project. This is an example workload
manifest.

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeWorkload
metadata:
  name: x86-logs
  namespace: ny
spec:
  deviceSelector:
    matchLabels:
      device.cpu-architecture: x86_64
  type: pod
  pod:
    spec:
      containers:
        - name: random-server
          image: quay.io/project-flotta/nginx:1.21.6
```
