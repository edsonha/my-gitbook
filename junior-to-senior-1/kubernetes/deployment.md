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

