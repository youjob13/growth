## Why do we need the Docker Compose?

Docker compose (Fig in original) - YAML instructions for multi-container apps orchestration. Under the hood it uses the appropriated docker commands.

## Compose files

Compose defines applications in YAML files.

- The `volumes` block defines volumes that Docker will create on the host's filesystem
- The `networks` block defines networks for the services
- The `services` block defines application microservices
  - `image` - tells Docker which image to use when creating containers for this service
  - `command` - specifies the command Docker will execute to start the app in every container it creates for this service (overrides CMD commands specified in images and Dockerfiles, appends to the ENTRYPOINT command)
  - `environment` - defines environment variables the app will use
  - `networks` - tells Docker to connect the service's containers to specified network (network should already exist or be defined in the `networks` top-level key)
  - `ports` - tells Docker to map <port-on-docker-host>:<port-inside-container>
  - `depends_on` - tells Docker to wait for the specified services to be running before starting this one
      - `condition` - ensures this service will only go live after the speicifed service is running and passed e.g. *healthcheck*
  - `volumes` - mount specified volume into this container
  - `deploy`
      - `resources`
          - `limits`
              - `memory` - memory allocation to this service's container
  - `healthcheck` - run the command to determine if the application is up and health.
 
  ## Deploy the app

  To start an application run the next command from the directory with your docker-compose.yaml file:
  ```sh
  docker compose up
  ```
        
