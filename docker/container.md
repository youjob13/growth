## What is the container?

Containers are read-write **run-time** instances of images. You can start one or more containers from a single image.
Containers should only run a single process.

<img width="451" height="238" alt="image" src="https://github.com/user-attachments/assets/247ddbe2-937d-40c2-ab3c-7f037e4f629d" />

## Container (OS virtualization) VS VMs (hypervisors hardware virtualization)

Similarity:
- Virtualization technologies for running applications;
- Start, stop, restart and delete containers like you can with VMs.

Differencis:
- VMs virtualize hardware (virtual CPUs, RAM, install an OS and then an app), while **containers virtualize OS**;
- VMs look and feel as physical server, while containers look and fell as regular OS;
- You have to install an OS on every VM, every OS consumes CPU, RAM and storage and longer to boost. Containers share a single OS on the host.
- Containers are **stateless** and **ephemeral**, whereas VMs are **long-running**;
- Containers are designed to be **immutable**.

<img width="523" height="315" alt="image" src="https://github.com/user-attachments/assets/a1a051ba-5fa4-4588-bd8a-2a76dfaf90b9" />

Benefits:
- Containers are smaller and more portable;
- You can run more containers;
- Containers start faster;
- Containers reduce the number of OS you need to manage;
- Containers present a smaller attack surface.

 In the past were less secure because containers share the same host kernel. Now container engines implement sensible default such as SELinux, AppArmor etc.

 ## Images and Containers

 Docker make `read-write` possible for containers by creating a thin **read-write layer** for each container and placing it on top of the shared image.
 <img width="486" height="270" alt="image" src="https://github.com/user-attachments/assets/66090caa-2239-4212-9c8b-00e06bbdd413" />

- When you make any changes, these get written to container read-write layer; 
- When you stop a container, Docker keeps the read-write layer and restores it when you restart the container. But if you delete a container, Docker deletes its read-write layer.

## How containers start apps

1) And `Entrypoint` instruction in the image;
2) A `cmd` instruction in the image;
3) A `cli` argument.

`Entrypoint` and `cmd` are optional metadata intructions where you can store the command you want Docker to run to start the default app.

`Entrypoint` can not be overriden on the CLI. Everything you pass in via the CLI will be appended to the Entrypoint as an argument.

`Cmd` are overriden by CLI arguments.

## Connecting to a running container

Use the next command to execute commands in running containers:

```sh
docker exec -it container-name sh
```

To automatically connects to a container main process.
```sh
docker attach
```

Containers only run while their main process is executing. Kill the main process === kill the container.

## Container Restart Policies

Container *restart policies* are a simple form of **self-healing** that allows the local Docker Engine to automatically restart failed containers.

Docker supports the following 4 policies per container:
- no (default)
- on-failure
- always
- unless-stopped

| Restart Policy | Non-zero exit code | Zero exit code | docker stop | daemon restart|
--------------------------------------------------------------------------------------
| no (default) | No | No | No | No | 

## Docker Debug (Pro, Team, Business subscription, only for Docker Desktop)

Docker Debug allows to get shell session to the container and run commands that aren't installed in the container.

1) ```sh
   docker login
   ```
2) ```sh
   docker debug <image|container>
   ```
