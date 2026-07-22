## What is Docker Engine?

The Docker Engine is a set of server-side components of Docker that run and manage containers.
It's like a car engine:
- A car engine is made from many specialized parts that work together to make car drive.
- A Docker Engine is made from many specialized tools that work together to create and run containers - the API, image builder, high-level runtime, low-level runtime, shims etc.

Simplified diagram focuses on the components that start and run containers:
<img width="471" height="240" alt="image" src="https://github.com/user-attachments/assets/80fc6e39-2b90-49fa-9e81-3c8abac1c42f" />

## The Docker Engine

<img width="651" height="467" alt="image" src="https://github.com/user-attachments/assets/eb040c51-3cce-40e8-92e2-56874a7d5497" />

## docker run under the hood

<img width="659" height="448" alt="image" src="https://github.com/user-attachments/assets/72c15493-3d15-4c72-8fa4-22b7f516202b" />

## daemon

The role of the daemon is to expose API.
It accepts docker client requests and forward them to the containerd by using REST over gRPC.

## containerd

Containerd is a high-level runtime, that manage creating, stopping containers, images, networks.
Via containerd Kubernetes comunicate with containers.

## shim

Shim is layer between containerd and container runtime. Shim makes containerd daemonless. So if containerd breaks container runtime won't fail.
Shim is a parent process for the container.
Shim allows container comunicate with containerd. Keep container STDIN and STDOUT streams open.
Shim allows to replace runc with other low-level runtimes.

## runc

runc one of the low-level runtime implementation of the OCI runtime-spec and expects to start containers from OCI-compliant bundles.
runc is responsible for comunication with host kernel (Linux kernel) to create a process for the container, create namespaces, cgroups, mount file system.
