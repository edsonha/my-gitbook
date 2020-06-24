# Pods

The main aim is to deploy our app / instance in the form of container on a set of machine configured as worker node in a cluster. However, kubernetes does not deploy container directly on worker node. The container is encapsulated into kubernetes object called pods.

A pod is a single instance of the application, smallest object you can create in kubernetes.

The simple set up will be one worker node in a kubernetes cluster, with a single instance of your application running in single docker container encapsulated in a pod.

When you scale up, where do you spin up the additional instance? You do not spin up the same instance in the existing pod. You either create a new pod with the same instance inside the existing worker node or if there is no more capacity in the existing worker node, you deploy another worker node with the pod inside in the cluster.

Pod usually have one-to-one relationship with container running your application. To scale up, you create a new pod and vice versa.

**Multi-containers pod**

Are we restricted to a single container in a single pod? No, we can have multi-containers pod provided that 

1.  It is not the same container of the same kind of instance. 
2. Applicable for helper container supporting the main container and helping the main container to do its work, for example data processing.

When a new pod is created, the main and helper container is created since they are part of the same pod and vice versa. The two containers inside the pods can also communicate with each other directly by referring each other as localhost since they shared the same network space. They can also share the same storage space as well.

So pod is used by kubernetes to do the following:

* a map of each main container and helper container and their connection through link and network
* create shareable volume between main and helper container in each pod
* monitor the state of the container whether it is alive or dead

Although technically pod is not required, it is good practice as you can react to future architectural changes.

**Deploying pods**

```text
kubectl run nginx --image=nginx
// deploy a docker container by creating a pod. 
// First it create pod automatically and deploy the instance of nginx image. 
// You need to specifiy the download from dockerhub by --image nginx
// In current state, the user cannot access nginx websever from outside
// you can however access it internally from the worker node.

kubectl get pods 
// see a list of pods avaialbe in our cluster

kubectl get pods -o wide 
// get two additional info about worker node deployment and IP address of the pod. 
// Each pod will have its own IP address

kubectl describe pods 
// get detailed info on pods
```

