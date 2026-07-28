## Create a Dockerfile

Run the next command to create Dockerfile with docker help. Docker recognize the current working directory as the *build context*:
```sh
docker init
```

Run the next command to build the image with your new Dockerfile

```sh
docker build -t <image-name> -f Dockerfile .
```

Run the next command to run your app from the newly created image:

```sh
docker run -d --name <container-name> -p 3000:3000 <image-name>
```

The -p 3000:3000 maps port *3000* on your Docker host to port *3000* inside the container to reach the app from a browser.

## Moving to production with multi-stage builds

When it comes to container images - **big is bad!**

- Big means slow;
- Big means more potential vulnerabilities;
- Big means a larger attack surface.

**CRITICAL NOTE**: Images should only contain the stuff **needed** to run applications in production - *multi-stage build*.

e.g.:
- **Stage 1** - builds an image with all the required build and compilation tools
- **Stage 2** - copies the app code into the image and builds it
- **Stage 3** - creates a small production-ready image containing only the compiled app and anything needed to run it

<img width="470" height="241" alt="image" src="https://github.com/user-attachments/assets/ff97ac1b-65fd-4c82-a30c-cb209ed0653b" />

Example on go:
<img width="607" height="396" alt="image" src="https://github.com/user-attachments/assets/3a9c74bb-15e5-49de-92b9-7b0e7b401403" />

## Docker's Build system

- **Client**: Buildx builder - is a CLI plugin. Activated every time you run a `docker build` command
- **Server**: BuildKit

Buildx can be configured to talk to multiple BuildKit instances (builders)

<img width="539" height="267" alt="image" src="https://github.com/user-attachments/assets/be9489ba-7f80-42b1-a0b1-8119c2fae3e1" />

When you run a `docker build` command:
- buildx interprets the command and sends the build request to the selected *builder*. This includes the Dockerfile, command line arguments, caching options, export options, and the build context (app and dependency list)
- The *builder* performs the build and exports the image. The Buildx client monitors the build and reports on progress.

**docker-container** driver utilizes QEMU to emulate target hardware, so its support more target platforms.

Docker's Build Cloud buider running in Build Cloud on native hardware and offer a shared cache so teammates can share a common cache for even faster builds.

## Good practices

- **Leverage the build cache** - BuildKit uses a cache to speed up builds. Layers and other artifacts from the first build are cached and leveraged by later builds. If you use a local builder the cache is only available to other builsd you execute on the same system. However, your entire team can share the cache on Docker Build Cloud. For each build the builder iterates through the Dockerfile one line at a time, starting from the top. For each line, it checks if it already has the layer in its cache. If it does, a *cache hit* occurs, and it uses the cached layer. If it doesn't, a *cache miss* occurs and it builds a new layer from the instruction. **Cache hits are one of the best ways to make builds faster.** Push instructions most likely to invalidate the cache go near the end of the Dockerfile. To skip cache use `--no-cache` option.
- **Only install essential packages** e.g. for node - `npm ci --omit=dev`
- **Clean up** - `docker rm <container>` and `docker rmi <images>`
