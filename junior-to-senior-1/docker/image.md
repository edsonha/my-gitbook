# Image

Docker Image file is called Dockerfile.

```bash
FROM node:8.11.1

CMD ["./bin/bash"]
```

The first command is to tell docker to use the node image from docker hub repo. We sometimes called this parent image.

The second command is to the CMD or command instruction tells us what to run in the container and this is to access its profile.

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

```

