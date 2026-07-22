## docker pull

To copy/update new image into Docker host.

```cmd
docker pull nginx:latest
```

## docker images

To see all docker images on the host.

```cmd
docker images
```

## docker run

To start a new container in detached mode `-d` called `nginxcontainer`. `-p` map Docker port `80` in the container to the host port `8080`.

```cmd
docker run --name nginxcontainer -d -p 8080:80 nginx:latest
```

## docker ps

To see running containers.

```cmd
docker ps
```

## docker exec

To execute a command inside the container.
To attach shell to a new Bash process inside the container:

```sh
docker exec -it nginxcontainer bash
```
