# Docker Registry

image: nginx    Under the hood, it is \(image: docker.io/nginx/nginx\) 

* docker.io is the registry 
* nginx \(1st\) is the user / account / organization 
* nginx \(2nd\) is the image / repository name

Docker registry is central repository of all docker images.

There is also private registry. To run the container in private registry, you need to login:

**docker login private-registry.io** and then, **docker run private-registry.io/apps/internal-app**

What if you are running your application on-premise and don't have private registry? Can you create custom private registry within your organization?

Yes, docker registry itself is another application and is avaiable as docker image. The name of the image is registry and it exposes the API on port 5000.

```text
docker run -d -p 5000:5000 -name registry registry:2
```

Now that you have your own custom registry running at port 5000 on the docker host, how do you push your own image? First use the docker image tag command to tag the image with the custom registry URL:

```text
docker image tag my-image localost:5000/my-image
Or
docker build . -t ${docker_username}/my-simple-webapp
```

And then I can push my image to my local private custom registry using command docker push

```text
docker push localhost:5000/my-image
OR
doker push ${docker_username}/my-simple-webapp
(May need to login using "docker login" to push to docker hub)
```

You can pull using docker pull localhost or IP / domain name of my docker host

```text
docker pull localhost:5000/my-image 
or
docker pull 192.168.56.100:5000/my-image
```

