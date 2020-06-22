# Dockerfile - Docker Image

Why you need to create your own image:

* because you cannot find a service you want to use as part of your application
* team decision that application will be dockerized for ease of shipping and deployment

How to create your own image:

* Write down the instructions for setting up your application in Dockerfile such as installing dependencies, where to copy the source code from and to, and what entry point of the application, etc

```bash
FROM node:8.11.1

WORKDIR /usr/src/smart-brain-api

COPY ./ ./

RUN npm install

CMD ["/bin/bash"]
ENTRYPOINT
```

FROM instruction defines what the base OS should be for this container. Every docker image must be based of another image either OS or image that was created before based on OS.

WORKDIR or working directory instruction is the directory in the container that we want to work out from.

COPY is to copy whatever we want from our current directory into the container.

COPY ./ ./ -- is to copy everything in root to root

COPY package.json ./ -- is to copy only package.json to root

RUN is what type of commands should we run in the container. RUN npm install is like how you git clone and you do npm install.

CMD or command instruction tells us what to run in the container and this is to access its profile.

Entrypoint specify a command that will be run when the image is run as container

**What is the difference between CMD and EntryPoint?**

How do you override CMD temporarily? by attaching command in the docker run. \(i.e. docker run ubuntu sleep 5\)

How do you make CMD change permanently? by changing the dockerfile and rebuilding it. You can still override it using the docker run \(i.e. docker run ubuntu-sleeper sleep 10\). But this is not good. Ideally we want to just pass the parameter \(i.e. docker run ubuntu-sleeper 10\).  That is when Entry Point come in.

For example, ENTRYPOINT\["sleep"\]. Because Entry Point is appended, you have to specifiy the number \(docker run ubuntu-sleeper 10\) or you will get an error \(operand is missing\).

To configure default value, you use both Entry point and CMD. Entrypoint will be appended to the terminal and the CMD is the default value that can be overwritten. But you have to write the entrypoint and CMD in JSON format \["sleep"\] and \["5"\] respectively

How to modify entry point at run time? by running, docker run --entrypoint sleep2.0 ubuntu-sleeper 10

**What's the difference between RUN and CMD?**

RUN is what we call an image build step. The state of the container after a run command will be committed to the docker image. So a Dockerfile can run many run commands to build the image that we want. On the other hand, CMD is something that executed by default after you launch the build image. So a Dockerfile can have only one comment and that usually comes at the end of file.

```bash
Build Image

docker build -t ${your chosen name} .

// to build docker image locally.
// t = tag; which you can name whatever you like
// . means it is to build everything
```

