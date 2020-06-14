# Docker Compose

Docker Compose to launch separate services under one command. So, it launches multiple container for each services: API Server, Postgres, Redis, etc. In other word, it orchestrate our application services during development.

```text
docker-compose build

docker-compose down
// Now just in case you have any containers running in the background or you need to take down anything

docker-compose up

docker-compose up --build
```





