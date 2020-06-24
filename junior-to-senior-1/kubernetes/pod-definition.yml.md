# pod-definition.yml

Kubernetes use yml file as input to create objects such as pod, replicaSet, deployment, service.

The yml file have 4 required fields 

* **apiVersion** =&gt; Version of Kubernetes API used to create the object. For example: POD -&gt; v1, Service -&gt; v1, ReplicaSet -&gt; apps/v1, Deployment -&gt; apps/v1
* **kind** =&gt; Type of object we are trying to create \(pod, replicaSet, deployment, service\)
* **metadata** =&gt; Data about the object \(Only two and any two that kubernetes expect like name, label, etc\). For labels, you can indicate any key value pair as you wish that can be used to for pod identification and grouping. For example, "type: front-end" is for front-end pods. 
* **spec** =&gt; ****For info about containers and image. ****There is different format for different object \(so check documentation\)

```text
kubectl create -f pod-definition.yml
```

