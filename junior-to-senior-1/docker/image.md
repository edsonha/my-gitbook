# Docker Command

Docker Image file is called Dockerfile.

```bash
FROM node:8.11.1

WORKDIR /usr/src/smart-brain-api

COPY ./ ./

RUN npm install

CMD ["/bin/bash"]
```

FROM is to tell docker to use the node image from docker hub repo. We sometimes called this parent image.

WORKDIR or working directory instruction is the directory in the container that we want to work out from.

COPY is to copy whatever we want from our current directory into the container.

COPY ./ ./ -- is to copy everything in root to root

COPY package.json ./ -- is to copy only package.json to root

RUN is what type of commands should we run in the container. RUN npm install is like how you git clone and you do npm install.

CMD or command instruction tells us what to run in the container and this is to access its profile.

**What's the difference between RUN and CMD?**

RUN is what we call an image build step. The state of the container after a run command will be committed to the docker image. So a Dockerfile can run many run commands to build the image that we want. On the other hand, CMD is something that executed by default after you launch the build image. So a Dockerfile can have only one comment and that usually comes at the end of file.

```bash
1. Build Image

docker build -t firstcontainer .

// to build docker image
// t = tag; which you can name whatever you like
// . means it is to build everything
```

```bash
2. Run Container

docker run -it firstcontainer

// And it will bring you inside the container environment after running the 
// container. We can see that inside the container, we have node (node -v).
// Root is the bash profile of our container. And hash value that is generated 
// randomly by docker to identify which containers is which.

root@dc43c98b31c9:/#
```

```bash
3. Run Container on the background

docker run -it -d firstcontainer
// Our container running in the background but we didn't go inside of it.

docker ps
// To see all the containers that are currently running, so you can have multiple 
containers

docker exec -it ${hash} bash
// To reference and run the container

docker stop ${hash}
// To stop container running in the background

docker run -it -p 3001:3001 firstcontainer
// -p it is called port binding or port forwarding. First port is container port 
// and the second port is host computer port.
// We need to do this because Container and Host Computer is isolated from each 
// other, so we need to tell the container to expose the port.
```

After creating API server using Docker container, we can give this folder with Dockerfile to anyone and as long as they have Docker, they can simply run this folder on any machine that we want.

