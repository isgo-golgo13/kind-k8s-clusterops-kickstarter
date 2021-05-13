# KinD K8s ClusterOps Spin-Up Guide

This guide shows how to spin up and operate the lifecycle of a Docker-in-Docker K8s cluster using KinD.
The offical KinD site is here: https://kind.sigs.k8s.io/ and the KinD quick start page is here:  https://kind.sigs.k8s.io/docs/user/quick-start/

### Install KinD (Unix/Linux)

To install the KinD Docker-in-Docker K8s local cluster, the preferred approach is to use ***`arkade`*** CLI. 

To install the arkade K8s CLI installer do the following:
```
curl -sLS https://dl.get-arkade.dev | sudo sh
```
The official github site for `arkdade` is here: https://github.com/alexellis/arkade

If arkade is installed or after arkdade is installed, to install KinD do the following:
```
arkade get kubectl --------> If and only if kubectl was not installed
arkade get kind
```

### Validate KinD installation and KinD installed version
```
kind version
```

The expected result of this validation should show (or a later v.X.X.X version tag):
```
kind v0.8.1 go1.14.4 darwin/amd64
```

### To Install and Create Ingress Controller for KinD

To create a KinD configuraion and install an ingress controller read the following:

https://kind.sigs.k8s.io/docs/user/configuration/ and https://kind.sigs.k8s.io/docs/user/ingress/


### Create a KinD K8s cluster
```
Syntax:
kind create cluster <--name=string> <--wait=duration (default is 0s)>
```
***Actual use:***

This will create a KinD K8s cluster with the cluster name as 'enginesvc-cluster' with a delayed wait time for spinup of 5 secs
```
kind create cluster --name enginesvc-cluster --wait 5
```

### Delete a KinD K8s cluster
```
Syntax:
kind delete cluster <--name=string> <--wait=duration (default is 0s)>
```
***Actual use:***

This will delete a KinD K8s cluster with the cluster name as 'enginesvc-cluster' with a delayed wait time for spinup of 5 secs
```
kind delete cluster --name enginesvc-cluster --wait 5
```
