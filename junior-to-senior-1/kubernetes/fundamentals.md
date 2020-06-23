# Fundamentals

**Kubernetes and Docker** 

Kubernetes use docker host to host the applications in the form of docker container.

**Node**

Node \(minions\) is a machine \(physical or virtual\) on which kubernetes software are installed. It is a worker machine and that is where containers will be launched by kubernetes.

A cluster is a set of nodes grouped together. Why you need a set of odes? If one node fail, you have other node to support.

**Master**

Master is responsible for managing this cluster and store information about the cluster's member, manage the workload, etc. The actual orchestration of containers on worker node.

When you install kubernetes on a system, you are actually installing these following components:

* API server - Front end for kubernetes \(CLI, etc\). All talks to API server to interact with kubernetes 

  cluster.

* etcd server - Distributed reliable key value. Store all data used to manage the cluster. It implements logs within the cluster to ensure there are no conflicts between the masters.
* kubelet service - Agent that runs on each node in the cluster. The agent is responsible for making sure that the containers are running on the nodes as expected. 
* container runtime - Underlying software that is used to run the containers. In this case, it is docker.
* controller - The brain behind the container orchestration \(i.e. monitor the health of the node and replace failed node\) 
* scheduler - Responsible for distributing works or container across multiple nodes. It looks for newly created containers and assign them to nodes

