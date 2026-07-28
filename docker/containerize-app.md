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

