---
layout: post
title:  "OSBuild operator for OS lifecycle management"
date:   2022-07-27 12:00:00 +0100
categories: flotta
author: Danielle Barda <dbarda@redhat.com>
tags:
  - osbuild
  - oslifecycle 

summary-1: OSBuild operator for OS lifecycle management
---

The OSBuild operator provides a kubernetes API by the means of new Custom Resource Definitions for building OSTree images as part of OS lifecycle management,
in flotta project.

The first release of the operator allows the user to build edge-container for RHEL images (RHEL >= 8.6) and make them accessible in S3 bucket.

Please see below the step-by-step guide for producing a new edge-container image.
A complete demo can be found [here](https://www.youtube.com/watch?v=SnNcHToCcDQ)

## Prerequisites installation
### Clone the osbuild-operator repository
```shell
git clone https://github.com/project-flotta/osbuild-operator.git
cd osbuild-operator
```

### Store a RHEL image in an accessible endpoint for creating osbuild-workers
Here we will use Nexus for storing a RHEL image and make it accessible for installing OSBuild-Worker VMs.     
Deploy Nexus operator by following the instruction [here](https://github.com/RedHatGov/nexus-operator#installation) 
and after deploying Nexus operator finished, create a new Nexus instance by running

```shell
oc apply -n osbuild -f config/creating_env/deploy_nexus.yaml
```

Install the Nexus CLI
```shell
pip install nexus3-cli
```

Login to Nexus
```shell
export CLUSTER_DOMAIN='mycluster.example.com'
oc get secret -n osbuild nexus-osbuild-admin-credentials -o jsonpath={.data.password} | base64 -d | xargs nexus3 login --url https://nexus-osbuild-osbuild.apps.${CLUSTER_DOMAIN} --no-x509_verify --username admin --password
```

Create a Hosted Raw repository named disk-images
```shell
nexus3 repository create hosted raw disk-images
```

Upload the rhel qcow2 image (it was tested with [RHEL 8.6](https://access.cdn.redhat.com/content/origin/files/sha256/c9/c9b32bef88d605d754b932aad0140e1955ab9446818c70c4c36ca75d6f442fe9/rhel-8.6-x86_64-kvm.qcow2?user=07786f290529f76887dfea2fc9631d69&_auth_=1659009182_73d2e99e48a4486633a014b63d7e3312))
```shell
nexus3 upload rhel-8.6-x86_64-kvm.qcow2 disk-images
```

### Create an S3 service
Deploy MinIO
```shell
oc apply -n osbuild -f config/creating_env/deploy_minio.yaml

```

Create a bucket name osbuild-images. You can use the aws cli (please follow the [installation instructions](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html))
```shell
export CLUSTER_DOMAIN='mycluster.example.com'
AWS_ACCESS_KEY_ID=minioadmin AWS_SECRET_ACCESS_KEY=minioadmin aws --endpoint-url https://minio-s3-osbuild.apps.${CLUSTER_DOMAIN} --no-verify-ssl s3 mb s3://osbuild-images
```

Create a secret for the S3 credentials
```shell
oc create secret generic osbuild-s3-credentials -n osbuild --from-literal=access-key-id=minioadmin --from-literal=secret-access-key=minioadmin

```
Create a secret for the CA Bundle using the OCP route
```shell
oc get secrets -n openshift-ingress-operator router-ca -o "jsonpath={.data.tls\.crt}" | base64 -d > /tmp/ca-bundle
oc create secret generic osbuild-s3-ca-bundle -n osbuild --from-file=/tmp/ca-bundle

```

### Create a Secret for your Red Hat Credentials

Find your Red Hat credentials and create a secret:
```shell
oc create secret generic redhat-portal-credentials -n osbuild --from-literal=username=<USERNAME> --from-literal=password=<PASSWORD>
```

### Create a PostgreSQL Server
Currently, the controller does not support creating the PostgreSQL server on its own, making this step mandatory

Edit the file `config/creating_env/psql.env` and set a real password

Create the PostgreSQL server by running 
```shell
oc new-app --env-file config/creating_env/psql.env postgresql:13-el8 -n osbuild
```

Edit the file `config/creating_env/postgress_secret.yaml` with the same password

Create new secret (please enter a real encoded password) 
```shell
oc create -f config/creating_env/postgress_secret.yaml
```

### Provision an External Worker VM using CNV
Create an SSH key-pair
```shell
ssh-keygen -t rsa -b 4096 -C cloud-user@external-builder -f ~/.ssh/external-builder
```

Create symlinks to the files to facilitate the next step
```shell
ln -s ~/.ssh/external-builder.pub config/creating_env/ssh-publickey
ln -s ~/.ssh/external-builder config/creating_env/ssh-privatekey
```

Generate the secret
```shell
oc create secret generic external-builder-ssh-pair --from-file=config/creating_env/ssh-privatekey --from-file=config/creating_env/ssh-publickey -n osbuild
```

Deploy the VM
```shell
oc apply -n osbuild -f config/creating_env/external-worker-vm.yaml
```

Get VM Address
```shell
oc get vmi external-builder -o jsonpath={.status.interfaces[0].ipAddress}
```


## Create OSBuildEnvConfig singleton CR ##
Apply OSBuildEnvConfig
```shell
export CLUSTER_DOMAIN='mycluster.example.com'
export EXTERNAL_WORKER_IP=`oc get vmi external-builder -o jsonpath={.status.interfaces[0].ipAddress}`
cat config/samples/osbuilder_v1alpha1_osbuildenvconfig.yaml | envsubst | oc apply -f -
```

## Create an edge-container image ##
Apply osbuildConfig that contains all the relevant configuration for running osbuild-composer job.
You can use that sample:
```shell
oc create -f config/samples/osbuilder_v1alpha1_osbuildconfig.yaml -n osbuild
```

After applying osbuildConfig CR you should see a new osbuild CR that was triggered automatically
```shell
oc describe osbuild osbuildconfig-sample-1 -n osbuild 
```

As part of that osbuild CR you can found the osbuild-composer job status, the job composer ID, and after finish running you also can found the containerUrl in the S3 bucket
```shell
  status:
    conditions:
    - message: Edge-container job is still running
      status: ""
      type: startedContainerBuild
    - message: Edge-container job was finished successfully
      status: ""
      type: containerBuildDone
    containerComposeId: 80125a8c-6e4a-42fe-8c06-8f90398fe5b1
    containerUrl: https://minio-s3-osbuild.apps.my-cluster.example.com/osbuild-images/composer-api-2ca271b8-1a9e-4bae-bcec-ab151c2bdc5b-container.tar?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=minioadmin%2F20220720%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220720T095954Z&X-Amz-Expires=604800&X-Amz-SignedHeaders=host&X-Amz-Signature=ac57b8499450dd4b62b80936277db89e7e850d5c3efab9e39bb9a493c064921f
```

## Run a VM using the newly created edge-container

### Upload the tar file to container image registry
Download the tar file to your local environment 
```shell
curl -k <containerUrl> -o /tmp/local.tar
```

Upload the image to your Container Registry using skopeo, pay attention that a Path Prefix might be required (e.g. your account name)
```shell
export IMAGE_NAME=<Container-Registry-URL>/osbuild:v1
skopeo login --username admin -p <PASSWORD> <Container-Registry-URL>
skopeo copy oci-archive:/tmp/local.tar docker://${IMAGE_NAME}
```

### Run the container using podman
Run the container
```shell
podman pull ${IMAGE_NAME}
podman run --detach --name osbuild-test -p 8080:8080  ${IMAGE_NAME}
```

Install a VM using a kickstart file that config the ostree to point to the running container
```shell
virt-install --name device --memory 4096 --vcpu 4 --disk size=8 --location <rhel-8.6-iso-location> --initrd-inject=/home/deploy/edgedevice.ks --extra-args="ks=file:/edgedevice.ks console=tty0 console=ttyS0,115200n8"
```

The kickstart file should contain  
```shell
ostreesetup --nogpg --url=http://<Host-Container-Machine-URL>/repo/ --osname=rhel --remote=edge --ref=rhel/8/x86_64/edge
```

Validate the rpm-ostre status is identical to the running container commit ID (from inside the VM)
```shell
curl -k http://<Host-Container-Machine-URL>/repo/refs/head/rhel/8/x86_64/edge
rpm-ostre status
```
