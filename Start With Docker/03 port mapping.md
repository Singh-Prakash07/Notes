### Port Mapping
+ Port mapping is the process of linking a port on the host machine to a port inside a Docker container.
+ This allows external traffic to reach a service running inside the container.
### How Port Mapping Works
+ By default, services running inside a container are isolated from the host machine's network. You can't access a web server running on port 80 inside a container just by navigating to localhost:80 on your host. Port mapping, also known as port publishing, creates a tunnel that redirects network traffic from a specified port on the host to a specific port in the container.
### Syntax and Example
+ You define port mapping using the -p or --publish flag with the docker run command.
+ Syntax: docker run -p <host_port>:<container_port> <image_name>
+ <host_port>: The port on your local machine that you want to expose.
+ <container_port>: The port that the application inside the container is listening on.
+ <image_name>: The name of the Docker image you are running.
### Example:
+ To run a Nginx web server container and access it from your host machine on port 8080,
 while the server inside the container is listening on its default port 80, you would use:
```
docker run -d -p 8080:80 nginx
```
+ This command maps port 8080 on the host to port 80 inside the nginx container.
  Now, you can access the Nginx welcome page by opening a web browser and navigating to http://localhost:8080.

### Automatic Port Mapping
+ Docker can also automatically map a container's exposed ports to a random, unused port on the host. This is useful when you don't care which host port is used, or when you're running multiple instances of the same service.
+ Syntax: docker run -P <image_name>
+ Example: docker run -d -P nginx
+ Docker will randomly assign a high-numbered port on the host (e.g., 32768) to port 80 in the container. To find out which port was assigned, you can use the docker ps command after the container is running.
+ -d flag stands for detached mode. It's an option you use when running a container to tell Docker to run it in the background.
### How It Works
+ When you run a container without the -d flag, the container's output is streamed directly to your terminal. Your terminal will be busy and you won't be able to enter other commands until the container's main process finishes.
+ However, when you use the -d flag, Docker starts the container and immediately sends it to the background. Your terminal is then freed up, and you can continue to use it for other commands. This is perfect for running services like web servers that are designed to run continuously
+ without -d `docker run -p 80:80 nginx`. 

### Enviroment Variable
+ An environment variable is a dynamic-named value that can influence the behavior of processes running on a computer. They are a way to pass configuration settings from the outside (the operating system or shell) into an application without hard-coding those values.

+ For example, instead of writing your application's code with a specific database password, you can use an environment variable named DB_PASSWORD. When the application starts, it reads the value from this variable. This makes it easy to change the password or other settings without modifying the code itself.

+ Docker containers are designed to be portable and reusable. Environment variables are a key tool for achieving this, as they allow you to customize a container's configuration without rebuilding the image.
### 1. The ENV Instruction in a Dockerfile
+ The ENV instruction in a Dockerfile sets an environment variable during the image build process. This variable will be available to all subsequent build steps and to any running container created from the image.
+ Syntax: `ENV <key>=<value>`
 ```
# Dockerfile
FROM node:18
WORKDIR /app
COPY . .
# Set the environment variable for the application
ENV NODE_ENV=production
CMD ["node", "server.js"]
```
+ In this example, the NODE_ENV variable is set to production for any container created from this image.

### 2.  The -e or --env Flag in docker run
+ The most common way to use environment variables is by passing them at runtime with the docker run command. This overrides any variables that were set in the Dockerfile.
+ Syntax: docker run -e <key>=<value> <image_name>
```
docker run -e DB_HOST=192.168.1.100 my-web-app
```
+ This command passes the DB_HOST variable with the value 192.168.1.100 to the my-web-app container.
+ This approach is highly useful for managing sensitive information like passwords or API keys, as you can avoid hard-coding them in your Dockerfile and pass them securely at runtime.
### 3. The --env-file Flag
+ For managing a large number of environment variables, you can store them in a file and pass the entire file to the container using the --env-file flag.
+ Syntax: docker run --env-file <file_path> <image_name>
+ First, create a file named db.env:
```
# db.env
DB_USER=root
DB_PASSWORD=secret
DB_NAME=mydatabase
```
+ Then, run the container:` docker run --env-file ./db.env my-db-client`
