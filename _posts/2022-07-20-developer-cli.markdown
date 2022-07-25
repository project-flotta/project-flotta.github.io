---
layout: post
title: "Flotta Developer CLI"
date: 2022-07-20 12:00:00 +1000
categories: flotta
author: Ariel Ireni
tags:
- guide
- flotta
- dev-cli

summary-1: Getting started with Flotta Developer CLI
---

Flotta Developer CLI was created to enable easy creation of edge devices and deploy predefine workloads on them.
The CLI creates edge devices as docker containers, therefore docker is a requirement for the CLI to work.
The CLI uses the local k8s cluster pointed by the `$KUBECONFIG` environment variable or `$HOME/.kube/config` to obtain
necessary information for the registration process.

To get started using the developer CLI, install the Flotta Developer CLI.
Packages are available for fc36, epel8 and epel9 at project-flotta COPR repository.
```shell
sudo dnf -y copr enable project-flotta/flotta-testing
sudo dnf -y install flotta-dev-cli
```

You may enable auto-completion for the CLI by running the following command:
```shell
flotta completion bash > /usr/share/bash-completion/completions/flotta
```
And by pressing the `TAB` key, you can use the auto-completion:
```shell
flotta <tab><tab><tab>
flotta
add         (Add a new flotta resource)                                   list        (List flotta resources)
completion  (Generate the autocompletion script for the specified shell)  start       (Start flotta resource)
delete      (Delete the flotta resource)                                  stop        (Stop flotta resource)
help        (Help about any command)
```

Now, you can easily add a new edge device by running:
```shell
$ flotta add device --name device1
device 'device1' was added 
```

You can view edge device `device1` under the list of the registered devices:
```shell
$ flotta list device
NAME		STATUS		CREATED		
device1		running		46 seconds ago	
```

Once you have a registered edge device, you can deploy workloads on it:
```shell
$ flotta add workload --device device1
workload 'nginx1-21-6-ygneqhis' was added to device 'device1'
```

To view list of workloads use:
```shell
$ flotta list workload
NAME			STATUS		CREATED		
nginx1-21-6-ygneqhis	Running		2 minutes ago	
nginx1-21-6-kkejlmol	Running		5 minutes ago	
```

You can also stop and start a registered device:
```shell
$ flotta stop device --name device1
edgedevice 'device1' was stopped 

# view stopped device status
$ flotta list device
NAME		STATUS		CREATED		
device1		exited		2 minutes ago

# start device
$ flotta start device --name device1
device 'device1' was started 

# view started device status
$ flotta list device
NAME		STATUS		CREATED		
device1		running		3 minutes ago	
```

Finally, if you wish to delete a device or workload, you can run:
```shell
# delete workload
$ flotta delete workload --name nginx1-21-6-kkejlmol
workload 'nginx1-21-6-kkejlmol' was deleted 

# delete device
$ flotta delete device --name device1
device 'device1' was deleted 
```
