# Replica Set

Controller is brain behind kubernetes process that monitor kubernetes objects and respond accordingly.

The use of replica set:

* Ensure high availability - replication controller help run multiple instances of a single pod in k8 cluster to avoid single point of failure. Does it mean we cannot have a single pod architecture? No, replication controller will bring up a new one when that single pod fails.
* Help with load balancing and scaling by create multiple pods to share the workload across them.

The replica set can replicate another pod of the same instance inside a worker node when the user load increase or create new worker node with new pod of the same instance \(meaning it can span across multiples worker nodes in the cluster\)

The difference between replication controller and replica set is the former is old method and replica set is new and recommend way, even though they have the same purpose.

![Example of replicaset-definition.yml](../../.gitbook/assets/1%20%286%29.png)

The most crucial part is the spec portion because it consist of three things:

* template - replica set use this template to create pods when one goes down. This has the same content as pod-definition yml file
* replicas - the number of replica you want to create
* selector \(mandatory\) - used to identify what pods are under its control and to be monitored

The use of selector

Even though you have indicated the pod profile in the template section, the selector helps replica set to manage pod that are not created as part of replica set creation, for example, existing pod that match the labels. So when there is no existing matching pods, it will create for you.

```text
kubectl create -f replicaset-definition.yml 
// create the replicaset based on the specification provided

kubectl get replicaset
// info about replicaset

kubectl delete replicaset myapp-replicaset 
// delete replica set and all underlying pods

kebectl delete pod ${pod name}
// delete pod

Two way to scale up or down:
1. Update yml file and run
kubectl replace -f replicaset-definition.yml

2. This way, but does not update the file automatically
kubectl scale --replicas=6 -f replicaset-definition.yml 
or
kubectl scale --replicas=6 replicaset myapp-replicaset
// replicaset is the object type
```

