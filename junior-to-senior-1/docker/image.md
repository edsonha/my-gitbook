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
docker run
// Run a container from an image with the latest version

docker run redis:4.0 
// Add a tag to run a specific version

docker run -it -d firstcontainer
// -d means will run in detach mode and let the container run in the background
// -it for interactivity (prompt and waiting for STDIN)

docker ps
// To see all the containers that are currently running in background
dockers ps -a 
// To check all running and exited containers

docker exec -it ${containerId or names} bash
// To run the running container in the background.

docker stop ${containerId or names}
// To stop container running in the background

docker rm ${containerId or names} 
// To delete exited container

docker images 
// To list of available images

docker rmi ${image name} 
// To remove images. Must ensure all dependencies are removed first

docker pull ${image name} 
// Will only pull the image and not run the container

docker inspect ${container name or container id}
// Give more detail on specific container in json format

docker logs ${container name or container id}
// logs for container running in the background (detached mode)
```

```bash
PORT Mapping or PORT binding or PORT forwarding

// How does users access the application via port 5000.
// What IP do users use to access in webbrowser
// Two ways:
1. One is to use the IP of the docker container. But this is internal IP that is 
only accessible within the docker container via browser.
2. Use IP provided by the docker host. For that you work, you need to do 
port mapping

docker run -p 80:3001 ${container name}
// 80 is docker host port. 3001 is docker container port. Meaning map port 3001 to
// port 80.
// The underlying host where docker is installed is called docker host or 
// docker engine
// We need to do this because Container and Host Computer is isolated from each 
// other, so we need to tell the container to expose the port.
// You can run multiple instances of the container on different port.
```

```bash
Data Persistance in docker container
When you run mySQL container, the data are stored inside /var/lib/mysql inside 
docker container. Remember that docker container has isolated filesystem and any 
changes to any files only happen within the container. If you remove the container,
the data inside it is also gone. To persist, you need mapping.

docker run -v /opt/datadir:/var/lib/mysql mysql
// This way when the docker container run, it mount the external directory to a 
// folder inside docker container. This way the data will be stored in the external 
// volume directory. Thus will persist even though you delete docker container.
```

After creating API server using Docker container, we can give this folder with Dockerfile to anyone and as long as they have Docker, they can simply run this folder on any machine that we want.

When you run an image, it exit immediately. Why? Because container is not supposed to host an operating system \(like VM\). It just run specific task or process such as instance of web server or application server or database, etc. Once the task is complete, the container exits. Only lives as long as the process inside it is alive.

