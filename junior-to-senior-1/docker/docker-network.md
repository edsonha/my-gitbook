# Docker Network

When you install docker, it creates 3 networks automatically: **bridge**, **none** and **host.**

Bridge is the default network a container get attached to. If you want attach another network, you can specify the network info:

* docker run ubuntu --network=none 
* docker run ubuntu --network=host

**Bridge Network**

Bridge network is private internal network created by docker on the host. Container attached to this network by default and they get internal IP address The container can access each other using this internal IP. To access any of these container externally, use port mapping. 

**Host Network**

Another way to access the container externally is to associate the container to the hosts network. This takes out any network isolation between the docker host and docker container, meaning because the container is using the host network to be accessible externally and not requiring any port mapping. In this case, you will not be able to run multiple instance on the same host on the same port as the ports are now common to all containers in the host network.

**None Network**

With the none network, the container is not attached to any network and does not have any access to the external network or other container. They run in isolated network.

**User-defined networks**

How do you group different container on different internal IP? By default docker only create one internal bridge network. We can have user-defined network using the command:

```text
docker network create  --driver bridge  --subnet 182.18.0.0/16 custom-isolated-network

docker network ls
// list all networks
```

The right way to connect between container \(i.e web container connect to mysql container\) is using the container name. Docker has embedded DNS that help resolve each other using the container name. The built-in DNS always run on 127.0.0.11

How does docker implement networking? Docker uses network namespaces that create a separate name space for each container. It then uses virtual Ethernet pairs to connect container together.

