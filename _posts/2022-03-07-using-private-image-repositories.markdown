---
layout: post
title:  "Deploying workloads with images from private repositories"
date:   2022-02-07 17:00:00 +0100
categories: flotta
author: Jakub Dżon
tags:
  - guide
  - flotta
  
summary-1: Deploying workloads with images from private repositories
---

Users can deploy their containerized workloads to edge devices using Flotta and very often images they want to use are 
not public and are available only for users or services having proper credentials. 

Flotta supports that use case and allows users to use private images in their `EdgeDeployments`; this post shows how to 
make use of that support by walking you through all the required steps.

### Prerequisites

1. `podman` installed
2. Private image repository (quay.io, for example)
3. Image of the workload to deploy
4. Running `EdgeDevice` labelled with `dc=home` 
 
#### Image of the workload to deploy

For the purpose of this walk-through we will use nginx server image (docker.io/nginx:1.14.2) as the one that would be put 
in a private quay.io repository. You can, of course, use any private container image repository.

1. Login to quay.io:
```bash
podman login quay.io
```
You will be prompted for your username and password:
```bash
$ podman login quay.io                                                                                                     
Username: xxxxxx
Password: ******
Login Succeeded!
```

1. Pull `docker.io/nginx:1.14.2`
```bash
podman pull docker.io/nginx:1.14.2
```

1. Tag `docker.io/nginx:1.14.2` with a private name
```bash
podman tag docker.io/nginx:1.14.2 quay.io/<your quay.io username>/nginx:1.14.2
```

1. Push `nginx:1.14.2` to quay.io
```bash
podman push quay.io/<your quay.io username>/nginx:1.14.2
```

### Deployment

#### Sanity check
Before we start using private repository feature of Flotta, let's see what happens when you try to deploy private image in a simple `EdgeDeployment`:
1. Confirm that you have an `EdgeDevice` labelled with `dc=home`
```bash
$ kubectl get edgedevice -l dc=home
NAME                                          AGE
fedora-54b9dd17-9971-11ec-bcee-7085c256610d   149m
```

1. Create the `EdgeDeployment` that will be deployed to each `EdgeDevice` with `dc=home` label
```shell
kubectl apply -f -<<EOF
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDeployment
metadata:
  name: nginx-deployment
spec:
  type: pod
  deviceSelector:
    matchLabels:
      dc: home
  pod:
    spec:
      containers:
        - name: nginx
          image: quay.io/jdzon/nginx:1.14.2
          ports:
            - containerPort: 80
              hostPort: 9090
EOF
```

1. Confirm that `nginx-deployment` pod wouldn't start on the edge device by checking deployment phase (not `Running`) and events reported for your `EdgeDevice` object: 
```shell
$ kubectl describe edgedevice
Name:         fedora-54b9dd17-9971-11ec-bcee-7085c256610d
Namespace:    default
Labels:       dc=home
              device.cpu-architecture=x86_64
...
Status:
  Deployments:
    Last Transition Time:  2022-03-07T10:35:53Z
    Name:                  nginx-deployment
    Phase:                 Created
...
Events:
  Type     Reason  Age                  From                       Message
  ----     ------  ----                 ----                       -------
  Warning  Failed  4m10s (x2 over 16m)  edgedeployment-controller  error playing YAML file: initializing source docker://quay.io/jdzon/nginx:1.14.2: reading manifest 1.14.2 in quay.io/jdzon/nginx: unauthorized: access to the requested resource is not authorized
```

#### Creating auth file secret
To use private container image, user needs to obtain credentials for their image repository - contents of the auth file generated when one executes
```bash
podman login quay.io
```

Usually that would be `$HOME/.docker/config.json` or `${XDG_RUNTIME_DIR}/containers/auth.json` file.

When you have the auth file, you need to create a kubernetes secret containing it under `.dockerconfigjson` key:
```bash
kubectl create secret generic pull-secret \
  --type=kubernetes.io/dockerconfigjson \
  --from-file=.dockerconfigjson=${XDG_RUNTIME_DIR}/containers/auth.json
```

The created secret will look similar to the following one:
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: pull-secret
data:
  .dockerconfigjson: ewoJImF1dGhzIjogewoJCSJxdWF5LmlvIjogewoJCQkiYXV0aCI6ICJabTl2SUdKaGNpQm1iMjhnWW1GeUNnPT0iCgkJfQoJfQp9Cg== 
type: kubernetes.io/dockerconfigjson
```

#### Deploying the workload

To deploy workloads with a private image stored in the repository, you need to instruct Flotta operator to use the 
secret with valid credentials for the repository hosting that image. You do that by referencing it in the EdgeDeployment 
specification, under `imageRegistries`:

```yaml
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDeployment
metadata:
  name: nginx-deployment
spec:
  ...
  imageRegistries:
    secretRef:
      name: pull-secret
  ...
```


After you update your `EdgeDeployment`:

```shell
kubectl apply -f -<<EOF
apiVersion: management.project-flotta.io/v1alpha1
kind: EdgeDeployment
metadata:
  name: nginx-deployment
spec:
  type: pod
  deviceSelector:
    matchLabels:
      dc: home
  imageRegistries:
    secretRef:
      name: pull-secret
  pod:
    spec:
      containers:
        - name: nginx
          image: quay.io/jdzon/nginx:1.14.2
          ports:
            - containerPort: 80
              hostPort: 9090
EOF
```
After the next heartbeat received from the device, you will see the phase of the deployment to be `Running`:
```shell
$ kubectl describe edgedevice
Name:         fedora-54b9dd17-9971-11ec-bcee-7085c256610d
Namespace:    default
Labels:       dc=home
              device.cpu-architecture=x86_64
...
Status:
  Deployments:
    Last Transition Time:  2022-03-07T08:37:12Z
    Name:                  nginx-deployment
    Phase:                 Running
...
```

Congratulations! Now you have your private container image running on your edge device! 