# Docker Cheatsheet
Docker is a platform that enables you to combine an app plus its configuration and dependencies into a single, independently deployable unit called a container.
## Images
- An image is a read-only template with instructions for creating a Docker container. 
- Often, an image is based on another image, with some additional customization.
- You might create your own images or you might only use those created by others and published in a registry. 
- To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. 
- Each instruction in a Dockerfile creates a layer in the image. 
- When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. 

### Publish image to Docker Hub
Before you can publish your image, you need to rename it so that Docker Hub knows that the image is yours. Run the following command to rename your image. Replace YOUR-USERNAME with your Docker ID.

```bash
docker tag docker/welcome-to-docker YOUR-USERNAME/welcome-to-docker
```

## Containers
- Containers are an isolated environment to run any code.
- A container is a runnable instance of an image. 
- You can create, start, stop, move, or delete a container using the Docker API or CLI. You can connect a container to one or more networks, attach storage to it, or even create a new image based on its current state.
- By default, a container is relatively well isolated from other containers and its host machine. You can control how isolated a container's network, storage, or other underlying subsystems are from other containers or from the host machine.
- A container is defined by its image as well as any configuration options you provide to it when you create or start it. 
- When a container is removed, any changes to its state that aren't stored in persistent storage disappear.

### Example docker run command
The following command runs an ubuntu container, attaches interactively to your local command-line session, and runs /bin/bash.

```bash
docker run -i -t ubuntu /bin/bash
```

## Volumes 
If you want to persist data even after a container is deleted, you can use a volume. A volume is a location in your local filesystem, managed by Docker.If you want to persist data even after a container is deleted, you can use a volume. A volume is a location in your local filesystem, managed by Docker.

**Example:**
To add a volume to your project, simply go to the compose.yaml
```yaml
todo-database:
    # ...
    volumes:
      - database:/data/db
                      
# ...
volumes:
  database:
```

In this example, the volumes element that is nested in **todo-database** tells Compose to mount the volume named database to **/data/db** in the container for the todo-database service.

The top-level volumes element defines and configures a volume named database that can be used by any of the services in the Compose file.
Now, no matter how often you delete and restart the container, your data is persisted and accessible to any container on your system by mounting the database volume. Docker will check for a volume and create one if there is none present.

## Docker Compose 
if a tool could start multiple containers with a single command. 


- **compose.yaml** file tells Docker how to run your application.

### Docker Compose Commands

| Command                 | Description                                                                                                               |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `docker compose up -d ` | Builds and runs all the services listed in the compose file. (The `-d` flag tells docker compose to run in detached mode) |
| `docker compose watch`  | Automatically update and preview your running services as you edit and save your code                                     |



## Bind Mounts
Docker isolates all content, code, and data in a container from your local filesystem.

If you want to access data on your system, you can use a bind mount. A bind mount lets you share a directory from your host's filesystem into the container.

Example to add a bind mount to a project:
```yaml
todo-app:
    # ...
    volumes:
      - ./app:/usr/src/app
      - /usr/src/app/node_modules
```


In this example, the volumes element tells Compose to mount the local folder ./app to /usr/src/app in the container for the todo-app service. This particular bind mount overwrites the static contents of the /usr/src/app directory in the container and creates what is known as a development container. The second instruction, /usr/src/app/node_modules, prevents the bind mount from overwriting the container's node_modules directory to preserve the packages installed in the container.
Now, you can take advantage of the container’s environment while you develop the app on your local system. Any changes you make to the app on your local system are reflected in the container.


## Containerizing your application
When working with containers, you usually need to create a Dockerfile to define your image and a compose.yaml file to define how to run it.

To help you create these files, Docker has a command called `docker init`. 


## Dockerfile

| Command   | Description                                                           |
| --------- | --------------------------------------------------------------------- |
| `FROM`    | The base image for the new image.                                     |
| `COPY`    | Copies files from the host system to the image.                       |
| `WORKDIR` | Sets the working directory for the rest of the Dockerfile.            |
| `RUN`     | Runs a command in the image.                                          |
| `CMD`     | The default command to run when starting a container from this image. |

