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

## docker attach

To automatically attach the container main process.

```sh
docker attach nginxcontainer
```

## docker stop

To stop container. It send a *SIGTERM* to the container PID 1 process and allows the container 10 seconds to gracefully quit. If the process hasn't cleaned up and stopped within 10 seconds, it sends a *SIGKILL* to force the container to terminate immediately.

```sh
docker stop nginxcontainer
```

## docker restart

To restart a stopped container

```sh
docker restart nginxcontainer
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

## docker network ls

To list docker networks

```sh
docker network ls
```

## docker volume ls

To list docker volumes

```sh
docker volume ls
```

## docker compose ls

To list docker apps running with compose

```sh
docker compose ls
```

## docker compose top

To run a docker compose top to list the processes inside each
container

```sh
docker compose top
```

## docker compose stop

To stop running containers in compose

```sh
docker compose stop
```

## docker compose down

To remove running containers in compose

```sh
docker compose down
```
