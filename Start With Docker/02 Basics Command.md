## Image
### Run an image
1. `docker run -it ubuntu` first it search the image locally, if not found download from docker hub. then run it.
2.  here it means in itractive mode, means we will be container enviroment.
3.  If we not use it. it will create container but we can't use cli of that enviroment.
4.  Whenever we run an image it always create a new container.
5.  how to find images
```
dockerimage ls
OR
docker images // list all images with (REPOSITORY name, TAG, IMAGE ID, CREATED, SIZE)
```
6. To remove an image we first need to delete all its container.

## Container
### To find the Container ID or Name
1. `docker container ls` or `docker ps // ps means process status` to list all active containers.
2. `docker container ls -a` or `docker ps -a` to list all containers including stopped ones.
3. `docker container ls -a -s` or `docker ps -a -s` to list all containers along with size.

### To stop an container
1. Graceful Shutdown (docker stop) `docker stop <container_name_or_id>`.
2. Forceful Termination (docker kill) `docker kill <container_name_or_id>`.
3. `exit` to exit an bash terminal in a container.

### Detach from the Container
+ + If you want to leave the container running in the background, you can detach from it.
+ + This allows the container's process to continue without being tied to your terminal.`
Press Ctrl + p followed by Ctrl + q`.
+ `docker stop <container_id_or_name>` to stop it.
### Deleting Images and Containers
+ To delete an image or container, you must use a specific command for each.
+ To delete a container, use docker rm <container_id_or_name>.
+ To delete an image, use docker rmi <image_id_or_name>.
+ Before removing image we must have to delete all containers of that image.

### Docker Command 
+ Docker commands are organized into different groups, each managing a specific type of Docker object. This modern structure helps organize a large number of commands under a clear, intuitive hierarchy.
+ The general syntax for all Docker commands is:
```
docker <command_group> <command> <options> <object_name_or_id>
```

1. docker container 
+ This is the central group for managing containers. It includes all commands related to creating, starting, stopping, and removing containers.
+ Syntax: docker container <command> <container_name_or_id>
Example:
```
docker container ls: Lists all running containers.
docker container ls -a: Lists all containers (running and stopped).
```
+ This group manages containers, so you'll always specify the container name or ID at the end of the command.
```
docker container run <container_name_or_id>: Creates and starts a new container from an image.
docker container stop <container_name_or_id>: Stops a running container.
docker container rm <container_name_or_id>: Removes a stopped container.
```
2. docker image
+ This group manages Docker images, which are the read-only templates for containers.
+ Syntax: docker image <command>
+ Example:
```
docker image ls: Lists all local images.
docker image prune: Removes unused images to free up disk space.
```
+ You need to specify the name and optional tag of the image you want to download. If you omit the tag, Docker will default to the latest tag.
```
docker image pull <image_name>[:<tag>]: Downloads an image from a registry like Docker Hub.

docker image build <image_name>[:<tag>]: Builds a new image from a Dockerfile.

docker image rm <image_name>[:<tag>]: Removes a local image.

```
3. docker volume 💾
+ This group is used to manage volumes, which are a way to persist data outside of a container's filesystem.
+ Syntax: docker volume <command>
+ Example:
```
docker volume create: Creates a new volume.
docker volume ls: Lists all volumes.
docker volume rm: Removes one or more volumes.
```
4. docker network 🌐
This group is for managing Docker networks. Networks allow containers to communicate with each other and with the host machine.
+ Syntax: docker network <command>
+ Example:
```
docker network ls: Lists all networks.
docker network create: Creates a new network.
docker network connect: Connects a container to a network.
```
5. docker system
This group contains commands for managing the entire Docker system, including cleanup and information retrieval.
+ Syntax: docker system <command>
+ Example:
```
docker system info: Displays system-wide information.
docker system df: Shows Docker disk usage.
docker system prune: Removes all unused containers, networks, images, and volumes to reclaim disk space.
```

