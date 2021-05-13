# KinD K8s ClusterOps Spin-Up Guide

This guide shows how to spin up and operate the lifecycle of a Docker-in-Docker K8s cluster using KinD.

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

### Create a KinD K8s cluster
```
Syntax:
kind create cluster <--name=string> <--wait=duration (default is 0s)>
```
***Actual use:***
```
kind create cluster --name enginesvc-cluster --wait 5
```

### Delete a KinD K8s cluster
```
Syntax:
kind delete cluster <--name=string> <--wait=duration (default is 0s)>
```
***Actual use:***
```
kind delete cluster --name enginesvc-cluster --wait 5
```
