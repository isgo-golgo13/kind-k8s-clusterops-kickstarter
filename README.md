# KinD K8s ClusterOps Spin-Up Guide

This guide shows how to spin up and operate the lifecycle of a Docker-in-Docker K8s cluster using KinD.

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
