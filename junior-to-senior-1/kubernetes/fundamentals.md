# Fundamentals





kubernetes can help you test new features of your application by only upgrading a percentage of these instances through AB testing method

Kubernetes open architecture provides support for many different network and storage vendors

Kubernetes support a variery of authentication and authorization mechanism

Kubernetes and docker Keubenetes use docker host to host the applications in form of docker container.

Kubernetes architecture / cluster consists of a set of nodes

Node \(minions\) is a machine \(physical or virtual\) on which kubernete software are intstalled

Node is a worker machine and that is where containers will be launched by kubernetes

What if the node on which the application is running fails So that is why you need more than one node. A clusteris a set of nodes grouped together . If one node fail, you have other node to support.

Who is responsbile for managing this cluster Where is the info of members of the cluster stored how are the node monitoeed How do you manage workload That is where a master come in... master is a node with the kubernetes control plane components isntalled The master watched over the nodes in the clustter and is reponsible for the actual orchestaration of ocntainers on worker node

When you install kubernetes on a system, you are actually installing these following components

* API server - acts as front end for kubernetest \(CLI, etc\). All talks to API server to interact with kubernetes cluster
* etcd server - distributed reliable key vlaue store all data used to manage the cluster. It implement lock within the cluster to ensure there are no conflicts between the masters
* kubelet service - agent that runs on each node in the cluster. the agent is responsibble for making sure that the contaienrs are runnign on the nodes as ecpected 
* container runtime - uderyling software taht is used to run the containers. In this case, it happend to be docker
* controller - the brain behing the orchestartion. REsponseible for noticing and responding when nodes , container, or end point goes down. It makes decsion to bring up new container in such cases
* scheduler - is responsible for distributing works or container across multiple nodes. It looks for newly created containers and assigne them to nodes



