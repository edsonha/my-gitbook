# Docker

The idea is to have project run on a different machine / environment without any errors. And this is where containers come in.

Companies uses micro-services and have their products composed of multiple layers. These layers can be considered services, each with their own container doing its own thing and communicating with each other to make the whole system work.

The problem with micro-services is each service may have its own requirements from different node versions to conflicting library dependencies. And when you add in the fact that every developer's machine and environment is different, it can be challenged to onboard new developers quickly or run this service on another machine. So, Docker helps us create these containers around our services.

![](../../.gitbook/assets/1.png)

**History**

Before we have Docker, we have Virtualization / Virtual Machines or sometimes we called sandbox environments. It contains a full fledged computer with its virtual hardware operating system and as you can see in this diagram it's like having many computer sitting on top of another computer. This solves the problem because the app can run in an environment that is consistent and predictable. The downside is less speed.

**Docker**

Docker containers wrap up the software in a complete file system that contains everything they needs to run. 

Advantages: 

* Lightweight compare to VM because instead of virtual OS, it rely on host OS.
* Can only run single application on each container.
* Can be scaled up easily as you create more and more containers and use container orchestration like Kubernetes 

Characteristics:

* Each container has an image - Docker use this to bundle your application into a standalone executable package that can live inside of a container. For example, we want a node server, so this image is read by docker and it generates container that run node server for us.
* Each container environment is isolated from host machines
* Docker Hub is similar to NPM in JS land - it provides a store-like website where you can search and download images to use
* Image also has a file system just like we have files on our computer and that's what we call a volume.

To summarize, Docker bundles your application into an image - a standalone executable package and Docker executes this image in this container and the environment inside the container is completely isolated from that of the host machine.

![Creating many containers as you scale up and use Load Balancer to distribute request](../../.gitbook/assets/2.png)

