### Docker Networking
+ Docker networking allows containers to communicate with each other and with the host machine. By default, when you run a container, Docker sets up a virtual network layer to ensure containers are isolated but can still communicate in a controlled way.

### Types of Docker Networks
+ Docker supports several network drivers for different use cases. You can create and manage these networks using the docker network command group.
### 1. Bridge Network
+ When you install Docker, it automatically creates a default network called bridge. Unless you specify otherwise, all new containers are connected to this network.
  1. Communication: Containers on the same bridge network can communicate with each other using their container names or IDs.
  2. Isolation: Containers on different networks cannot communicate with each other.
  3. Host Access: To access a service in a container from your host machine, you must use port mapping to expose the container's port to the host.
+ **Example**: `docker run --name my-container --network bridge my-image`
### 2. Host Network
+ This driver removes network isolation between the container and the host. The container shares the host's networking stack, and its services are directly accessible via the host's IP address.
+ Use Case: Best for performance-critical applications that need minimal network overhead.
+ Container don't need to port mapping from container to host.
+ **Example**: `docker run --name my-container --network host my-image`.
### 3. None Network
+ This network driver disables all networking for the container. The container will have no network interfaces and cannot communicate with the outside world.
+ Use Case: When you need a highly secure, isolated environment.
+ **Example**: `docker run --name my-container --network none my-image`.
### 4. User-Defined Bridge Networks
+ It's best practice to create your own bridge networks instead of using the default one. User-defined networks offer better isolation, automatic DNS resolution, and are more scalable.
+ Command: `docker network create --driver bridge my-custom-network`
+ container with same network name can communicate with each other.
+ **Example**: `docker run --name my-container --network my-custom-network my-image`.
### Commands for Network Management
+ `docker network ls`: Lists all Docker networks on the host.
+ `docker network create`: Creates a new network with a specific driver.
+ `docker network inspect bridge(name of network)`: Provides detailed information about a network, including which containers are connected to it.
+ `docker network connect`: Connects a running container to a network.
+ `docker network disconnect`: Disconnects a container from a network.

### volume mounting
+ Volumes are the preferred method for persisting data in Docker. They provide a way to store data outside of a container's writable layer, which is essential for preserving data even if the container is stopped, removed, or replaced
+ A volume is a special directory on the host machine that is mounted into a container's filesystem. It's managed entirely by Docker. Unlike bind mounts, which can link any directory on the host, volumes are created and managed with Docker commands, making them more portable and secure.
### Types of Volumes
### 1. Named Volumes
+ Named volumes are the most common type. They are managed by Docker and stored in a specific directory on the host `(/var/lib/docker/volumes/` on Linux). You reference them by a unique name.
+ Best for: Storing database files, application state, and persistent data that needs to be backed up or shared between multiple containers.
+ Command: `docker run -v <volume_name>:<container_path> <image_name>`
+ Example:
```
# Create a volume named 'db_data' and mount it to /var/lib/mysql in the container
docker run --name my-mysql -v db_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=secret -d mysql
```
+ This command ensures that even if you delete the my-mysql container, the database data stored in the db_data volume will remain.

### 2. Anonymous Volumes
+ Anonymous volumes are similar to named volumes but are not given an explicit name. They are managed by Docker but can be harder to reference and clean up.
+ Best for: Temporary data storage where the data doesn't need to be persisted for long.
+ Command: `docker run -v <container_path> <image_name>`
+ Example: `docker run -it -v /app/data ubuntu bash`
+ This command creates an anonymous volume and mounts it at /app/data inside the container.

### Volume Commands
+ docker volume create <name>: Creates a named volume.
+ docker volume ls: Lists all volumes.
+ docker volume inspect <name>: Shows detailed information about a volume.
+ docker volume rm <name>: Removes a volume.
+ docker volume prune: Removes all unused local volumes to free up disk space.

