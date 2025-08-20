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
