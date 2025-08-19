## Image
### Run an image
1. `docker run -it ubuntu` first it search the image locally, if not found download from docker hub. then run it.
2.  here it means in itractive mode, means we will be container enviroment.
3.  If we not use it. it will create container but we can't use cli of that enviroment.
4.  Whenever we run an image it always create a new container.
5.  how to find images
```
docker images  // list all images along with (REPOSITORY name, TAG, IMAGE ID, CREATED, SIZE)
```
6. To remove an image we first need to delete its all container.
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
