---
layout: post
title:  "Running Ansible Playbooks on Edge Devices"
date:   2022-09-28 12:00:00 +0100
categories: flotta
author: Gloria Ciavarrini <gciavarrini@redhat.com>
tags:
- flotta
- devices
- ansible

summary-1:
---
There may be cases n which you would like to be able to execute a scripts or commands in a device or on a group of devices.
_Project Flotta_ makes your life easier by supporting _Ansible_ playbook execution.
How can we create an _Ansible_ playbook for the edge devices? How does the execution work in _Project Flotta_?
his is what we will cover in this blog post.

# Preliminary steps
## 1- Define the Ansible Playbook
First things first: we need to write your example _Ansible_ playbook.
To keep things easy, let's say we want to create a txt file in some of our edge devices.

```yaml
---
-  name: Hello Ansible Playbook
   hosts: 127.0.0.1
   gather_facts: false
   
   tasks:
   - name: Create a file called '/tmp/hello.txt'
     copy:
       content: Hello from Project Flotta!
       dest: /tmp/hello.txt
```

## 2 - Define the EdgeConfig
Then, it's time to send it to the _Flotta Operator_ but... How?
Easy! Let create an `EdgeConfig` CR! \
(See [CRD Reference](https://project-flotta.io/documentation/v0_2_0/operations/crd.html#edgeconfig) for detailed description).

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeConfig
metadata:
  name: edgeconfig-sample
spec:
    edgePlaybook: 
        playbooks: 
            - content: LS0tCi0gIG5hbWU6IEhlbGxvIEFuc2libGUgUGxheWJvb2sKICAgaG9zdHM6IDEyNy4wLjAuMQogICBnYXRoZXJfZmFjdHM6IGZhbHNlCiAgIAogICB0YXNrczoKICAgLSBuYW1OiBDcmVhdGUgYSBmaWxlIGNhbGxlZCAnL3RtcC9oZWxsby50eHQnCiAgICAgY29weToKICAgICAgIGNvbnRlbnQ6IEhlbGxvIGZyb20gUHJvamVjdCBGbG90dGEhCiAgICAgICBkZXN0OiAvdG1wL2hlbGxvLnR4dAo=
              timeoutSeconds: 10
```

The `content` item contains the `base64` encoding of our example playbook. It can be obtained using:

```bash
>> base64 << EOF
---
-  name: Hello Ansible Playbook
   hosts: 127.0.0.1
   gather_facts: false
   
   tasks:
   - name: Create a file called '/tmp/hello.txt'
     copy:
       content: Hello from Project Flotta!
       dest: /tmp/hello.txt
EOF
```
## 3 - Label the edge devices
To let the _Flotta Operator_ know that you want execute your `edgeconfig-sample` on one more specific edge devices, you must label them.

```bash
>> kubectl label edgedevice device1 config/device-by-config=edgeconfig-sample
>> kubectl label edgedevice device3 config/device-by-config=edgeconfig-sample
```
In this case, we want to run the playbook on two edge devices: `device1` and `device3`
## 4 - Apply the EdgeConfig to the cluster

```bash
>> kubectl apply -f edgeconfig-sample.yaml
```

# Architecture
What happens when _Flotta Operator_ receives the `EdgeConfig`?

It automatically creates a `PlaybookExecution` CR for each device that has been properly labelled.

<img src="/assets/images/architecture_ansible_support.png" alt="High level architecture of Ansible support" width="1100"/>

In this way it is possible to monitor the execution of the playbook on each edge device, indeed the edge device will update the status of the `PlaybookExecution` CR according with the Ansible playbook execution result.

The possible statuse are: `Deploying`, `Running`, `SuccessfullyCompleted`, `CompletedWithError`.

# Future works

At the time of writing of this blog post some important features are still missing.
For example, when does the _Flotta Operator_ can consider the `EdgeConfig` *completed*?

What if the user select 100 edge devices and some successfully completed the executions, others are no reachable and other completed the execution with errors?

We need to implement a "*waiting strategy*". The `EdgeConfig` has been designed to use `conditions`: in this way it possible to way until all the `PlaybookExecution` CRs are in a final state (`SuccessfullyCompleted` and `CompletedWithError`), or considered the `EdgeConfig` successfully executed if at least x% of the edge devices ran the playbook correctly.

This is a good opportunity for you to start contributing on _Project Flotta_!
