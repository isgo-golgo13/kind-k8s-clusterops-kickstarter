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

* https://kind.sigs.k8s.io/docs/user/configuration/
* https://kind.sigs.k8s.io/docs/user/ingress/


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


### Create Multi-Node and Multi-Node (HA) High Availability Clusters

To create multi-node (one control-plane node, N worker nodes) clusters or multi-node HA (min three control-plane nodes, min three worker nodes) cluster, KinD uses a **YAML** config file (a cluster-config.yaml file stored on disk and passed to the `kind create cluster` CLI.

#### Multi-Node (One Control Plane Node, Three Worker Node) Cluster

In a stored `cluster-config.yaml` file for this kind of cluster.

```
# four node (one control plane node, three worker nodes) cluster config
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker
- role: worker
```

Create this cluster as follows:

```
kind create cluster --name enginesvc-cluster --config ./cluster-config.yaml --wait 5
```
To get info on the cluster just created do the following:

```
kind get clusters
```

To get info on the cluster nodes just created do the following:

```
kind get nodes
```


#### Multi-Node HA-High Availability (Min Three Control Plane Nodes, Min Three Worker Node) Cluster

In a stored `cluster-config.yaml` file for this kind of cluster.

```
# six node (three control plane nodes, three worker nodes) HA cluster config
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: control-plane
- role: control-plane
- role: worker
- role: worker
- role: worker
```

Create this cluster as follows:

```
kind create cluster --name enginesvc-cluster --config ./cluster-config.yaml --wait 5
```
To get info on the cluster just created do the following:

```
kind get clusters
```

To get info on the cluster nodes just created do the following:

```
kind get nodes
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
