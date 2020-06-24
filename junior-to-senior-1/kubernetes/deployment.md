# Deployment

In production,  you usually only create deployment definition yml file \(no need for pod definition and replica set definition\). Because deployment automatically create replicate set and pod, so you have all their benefits and extra benefit of deployment as follow:

* Upgrade seamlessly by rolling update
* Roll back when necessary
* Pause, make changes and resume so that the changes are rolled out together. These changes are multiple command such as upgrading the underlying web server version and modify resource allocation. So you do not want to apply the changes immediately after each command

![](../../.gitbook/assets/2%20%284%29.png)

Deployment is higher rank than the replica set.

```text
kubectl create -f deployment-definition.yml

kubectyl describe deployments

kubectl get deployment myapp-deployment

kubectl get all
```

**Rollout and Versioning**

When you are doing deployment, under the hood you are triggering a roll-out that create a new deployment revision \(Revision 1, 2 and so on\). This numbering helps us keep track of versioning and in case a roll-back is necessary. 

```text
kubectl rollout status deployment/myapp-deployment
// get status of rollout 


kubectl rollout history deployment/myapp-deployment
// info on revision and history of rollout and change-cause
```

There are 2 deployment strategy:

1. Recreate - destroy all pods and then subsequently bring back all at once. Downside is application is down.
2. Rolling update \(default\) - upgrading seamlessly one by one

**Update your deployment** 

Once you make necessary changes to the definition file, run command

```text
kubectl apply -f deployment-definition.yml 

or

kubectl set image deployment/myapp-deployment nginx-container=nginx:1.9.1
// but does not change the definition file
```

![Under the hood, upgrade is creating another replica set and replacing the pod one by one](../../.gitbook/assets/1%20%285%29.png)

```text
kubectl get replicaset
// to find out that there are 2 replicasets

kubectl rollout undo deployment/myapp-deployment
// rollback to previous revision

kubectl create -f deployment-definition.yml --record
// intialize first deployment and record the change-cause
```

kubectl run nginx --image=nginx command is actually not just creating pod, but create deployment. You can do deployment this way, but the recommended way is to use definition file for easier revision in the future.

