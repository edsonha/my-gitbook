# Networking

There is IP address for the node and each node has their own IP address.

![](../../.gitbook/assets/2%20%284%29.png)

When kubernetes is initially configured, it create internal private network with 10.244.0.0 and all pods are tagged to this network using different number like 0.1, 0.2 and so on. Pods can talk to each other using this IP, but accessing another pod using the IP address may not be a good idea as IP is subject to change when recreating

What happen if you have multiple nodes in a cluster? Because when kubernetes set up a cluster, it does not set up networking automatically, so this create IP conflict.

Kubernetes expect us to set up networking that meet these criteria:

* All containers / pods can communicate to one another without NAT 
* All nodes can communicate with all container in cluster and vice versa without NAT 

Fortunately we do not have to set it up on our own as there a pre-build solution. With the pre-build solution, it manage the network and IP in my nodes and assign different network address for each network in the node . This create a virtual network of all pods and nodes where they are assigned unique IP address and using simple routing technique , the cluster networking enable communication between different node or pods to meet kubernetes requirement.

![](../../.gitbook/assets/3%20%282%29.png)

