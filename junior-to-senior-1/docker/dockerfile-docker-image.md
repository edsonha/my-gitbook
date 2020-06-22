# Dockerfile - Docker Image

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

