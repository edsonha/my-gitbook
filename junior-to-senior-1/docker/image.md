# Image

Docker Image file is called Dockerfile.

```bash
FROM node:8.11.1

CMD ["./bin/bash"]
```

The first command is to tell docker to use the node image from docker hub repo. We sometimes called this parent image.

The second command is to the CMD or command instruction tells us what to run in the container and this is to access its profile.

```bash
docker build -t firstcontainer .

// to run docker build
// t = tag; which you can name whatever you like
// . means it is to build everything
```

```bash
docker run -it firstcontainer

// And it will bring you inside the container environment after running the 
// container. We can see that inside the container, we have node (node -v).
// Root is the bash profile of our container. And hash value that is generated 
// randomly by docker to identify which containers is which.

root@dc43c98b31c9:/#
```

