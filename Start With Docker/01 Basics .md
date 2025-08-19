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
4.  
