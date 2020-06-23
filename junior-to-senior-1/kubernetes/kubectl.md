# Kubectl

```text
kubectl run --replicas=1000 my-web-server
// run thousand replicas of my-web-server

kubectl scale --replicas=2000 my-web-server
// for scaling up

kubectl rolling-update my-web-server --image=web-server:2
// rolling upgrade 

kubectl rolling-update my-web-server --rollback
// roll back upgrade

kubectl run hello-minikube 
// used to deploy an application on the cluster

kubectl cluster-info 
// view information about the cluster

kubectl get nodes 
// use to list all the nodes part of the cluster
```

