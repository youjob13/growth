## docker pull

To copy/update new image into Docker host.

```sh
docker pull nginx:latest
```

## docker images

To see all docker images on the host.

```sh
docker images
```

## docker build

To build new image from Dockerfile

```sh
docker build -t test:latest .
```

## docker run

To start a new container in detached mode `-d` called `nginxcontainer`. `-p` map Docker port `80` in the container to the host port `8080`.

```sh
docker run --name nginxcontainer -d -p 8080:80 nginx:latest
```

## docker ps

To see running containers.

```sh
docker ps
```

To list all containers, event in the stopped state

```sh
docker ps -a
```

## docker exec

To execute a command inside the container.
To attach shell to a new Bash process inside the container:

```sh
docker exec -it nginxcontainer bash
```

## docker stop

To stop container

```sh
docker stop nginxcontainer
```

## docker rm

To delete container

```sh
docker rm nginxcontainer
```

## docker rmi

To delete image

```sh
docker rmi nginxcontainer
```

## docker buildx

To build images (with multi-architecture as well)

```sh
docker buildx 
```

