---
name: Docker Manual
categories: ["Manual"]
tags: ["Manual"]
---

## image

build a image, tag it **service:1.0**, Dockerfile is in current directory **.**.
```sh
docker build -t service:1.0 .
```

show images
```sh
docker images
```

delete a image with tag or image id
delete a image with tag **service:1.0**
```sh
docker image rm service:1.0
```

## container

--name service: create a container, name it **service**
-p 7890:7890: map the container port 7890 to localhost 7890
-d: in detached mode
run a image with tag **service:1.0** in the **service** container
```sh
docker run --name service -p 7890:7890 -d service:1.0 service:1.0
```

list all containers
```sh
docker container ls -a
```

stop the running container with name or container id
stop the container named **service**
```sh
docker stop service
```

start a container named **service**
```sh
docker start service
```

remove a container named **service**
```sh
docker container rm service
```

enter a container named **service**
```sh
docker exec -it service sh
```