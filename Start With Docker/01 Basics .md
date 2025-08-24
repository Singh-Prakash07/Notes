### Docker
+ Docker is a platform that uses OS-level virtualization to deliver software in packages called containers.
+ It's an open-source tool that simplifies the process of building, shipping, and running applications. 

### Key Concepts
#### Containers: 
A container is a lightweight, standalone, executable package of software that includes everything needed 
to run an application, including the code, a runtime, system tools, system libraries, and settings. Unlike virtual machines (VMs), containers share the host operating system's kernel, making them much more efficient and faster to start up.

#### Docker Engine:
This is the core of Docker. It's a client-server application that consists of three main components:
a Docker daemon (the server), a REST API, and a command-line interface (CLI) client.
The daemon builds, runs, and manages Docker containers.

#### Docker Images: 
An image is a read-only template with instructions for creating a Docker container.
You can think of it as a blueprint for a container. Images are built from a Dockerfile.

#### Dockerfile: 
This is a simple text file that contains a set of instructions for building a Docker image.
It specifies the base operating system, the application code, dependencies, 
and commands to run the application.

| Object-Oriented Programming | (OOP)	Docker |
| ------------------------------|-------------- |
| Class (Blueprint)	| Image (Template) |
| Object (Instance of a class)	| Container (Instance of an image) |
| new MyClass()	| docker run myimage |
| myObject.doSomething()	| docker exec mycontainer mycommand |

#### Installing
1. After installing in ubuntu we need to add user to docker groups
```
sudo usermod -aG docker $USER // either reboot system or use below command(wethout reboot)
newgrp docker
```
2. we need to use sudo for before every docker command .

### How to Build a Docker Image
+ Building an image is done using the docker build command and a Dockerfile. The Dockerfile is a plain text file that contains a series of instructions that tell Docker how to build the image.
+ Example Process:

  1. Create a Dockerfile in the root directory of your project. 
  2. Define the steps to set up your application. For example:
  3. Run the docker build command from your terminal:
  ```
  docker build -t my-app:1.0 .
  -t: Tags the image with a name (my-app) and version (1.0).

  .: Specifies the build context, which is the current directory where the Dockerfile is located.
  ```
+ This process creates a single, self-contained image that can be shared and run anywhere Docker is installed.
### What is Docker Compose
+ Docker Compose is a tool for defining and running multi-container Docker applications. While docker run is great for a single container, real-world applications often need multiple services to work together (e.g., a web app, a database, and a cache). Docker Compose simplifies this by using a YAML file to configure all of your application's services.

### Why We Need a Compose File
+ A docker-compose.yml file serves as a single source of truth for your entire application's configuration. It helps with:
+ Orchestration: Starts, stops, and links multiple services with a single command (docker compose up).
+ Reproducibility: Ensures that everyone on your team, or your production server, can run the application with the exact same setup.
+ Configuration: You can declare networks, volumes, port mappings, and environment variables in one place, which is far easier than managing multiple long docker run commands.

### How to Write a Compose File
+ The file uses a simple, human-readable YAML syntax.
#### Key components:
1. services: Defines the containers (e.g., web, database, cache).
2. build or image: Tells Compose whether to build an image from a Dockerfile (build) or to pull a pre-built image from a registry (image).
3. ports: Maps ports from the host to the container.
4. volumes: Persists data between container runs.
5. networks: Allows services to communicate with each other.
+ Here's a simple docker-compose.yml file for a Node.js app and a Redis cache:
Docker Compose Example
```
version: '3.8'

services:
  web:
    # Builds the image from the Dockerfile in the current directory.
    build: .
    ports:
      - "8080:3000"
    # Connects this service to the network named 'app-network'.
    networks:
      - app-network

  redis:
    # Pulls a pre-built Redis image from Docker Hub.
    image: "redis:alpine"
    networks:
      - app-network

# Defines the network so 'web' and 'redis' can talk to each other.
networks:
  app-network:
    driver: bridge

```
+ With this single file, you can:
1. Start the entire application stack: `docker compose up`
2. Stop all services: `docker compose down`
3. Rebuild and restart services: `docker compose up --build`
4. View logs from all services: `docker compose logs`
5. Run a one-off command in a service: `docker compose run web npm test`
+ In short, Docker Compose takes the pain out of managing complex, multi-container applications by treating your entire setup as a single unit. It's the essential next step after you've mastered creating a single Docker image.

|Command | Primary Action |	Goal / Purpose	| Output |
|-------|-----------------|-----------------|--------|
| `docker compose build`	| Builds the Docker image(s). |	To create the reusable, static image that contains your application and its dependencies. |	One or more Docker Images stored locally. No containers are started. |
| `docker compose up` |	Runs the application stack.	 |To create and start the live, running containers based on the images, applying runtime settings (ports, volumes, networks).	| One or more running Docker Containers. |
### creating image using compose file
```
version: '3.8'

services:
  web:
    # This line tells Docker Compose to build the image from the
    # Dockerfile in the current directory.
    build: .
    # This line tags the resulting image with the specified name.
    image: my-web-app:1.0
```
