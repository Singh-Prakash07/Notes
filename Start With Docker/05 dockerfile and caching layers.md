### Dockerfile
+ A Dockerfile is a simple text file that contains a series of instructions and arguments used to automatically create a Docker image. Each instruction creates a new, read-only layer in the image.
+ **Purpose**: To define the environment, dependencies, code, and configuration required to run an application consistently.
+ **Location**: Usually placed in the root directory of your project.

### Essential Dockerfile Instructions
1. FROM
+ Defines the base image for your build. Every Dockerfile must start with FROM.
+ Syntax: `FROM <image>[:<tag>]`
+ Example: `FROM ubuntu:22.04` (Starts from the specified Ubuntu base image)
> [!Note]: Use slim, Alpine, or minimal images (like node:18-alpine) to keep image size small.

2. RUN
+ Executes any commands in a new layer on top of the current image. This is typically used for installing software packages and dependencies.
+ Syntax: `RUN <command>`
+ Example: `RUN apt-get update && apt-get install -y python3`
+ Best Practice: Combine multiple commands into a single RUN instruction using && and include cleanup (e.g., rm -rf /var/lib/apt/lists/*) to reduce the number of layers and image size.

3. COPY
+ Copies files or directories from your local host machine (where you run docker build) into the new image filesystem.
+ Syntax: `COPY <source> <destination>`
+ Example: `COPY ./app /usr/src/app` (Copies the local app directory into /usr/src/app in the image)

4. ADD
+ Similar to COPY, but has extra features like automatically extracting compressed files (tar, gzip) from the source into the destination. COPY is generally preferred unless you need the archive extraction feature.
+ Syntax: `ADD <source> <destination>`

5. WORKDIR
+ Sets the working directory for any subsequent RUN, CMD, ENTRYPOINT, COPY, or ADD instructions.
+ Syntax: `WORKDIR /path/to/workdir`
+ Example: `WORKDIR /app `(All following commands will execute relative to /app)

6. EXPOSE
+ Informs Docker that the container listens on the specified network ports at runtime. This is documentation only; it does not actually publish the port. Port publishing must be done using the -p flag in docker run.
+ Syntax: `EXPOSE <port> [<port>...]`
+ Example: `EXPOSE 8080`

7. ENV
+ Sets environment variables, which are key-value pairs available to processes running inside the container.
+ Syntax: `ENV <key>=<value>`
+ Example: `ENV NODE_ENV=production`

8. CMD
+ Provides defaults for executing a container. Only the last CMD instruction in a Dockerfile takes effect. If the user provides an argument to docker run, the CMD instruction is overwritten.
+ Syntax: `CMD ["executable", "param1", "param2"]` (Preferred "exec" form)
+ Example: `CMD ["node", "server.js"]` (Runs the Node.js server)

9. ENTRYPOINT
+ Defines the core executable that will always run when the container starts. Any arguments provided in docker run or by the CMD instruction are passed as arguments to the ENTRYPOINT. It's often used to set up configuration or wrapper scripts.
+ Syntax: `ENTRYPOINT ["executable", "param1"]`
+ Example: `ENTRYPOINT ["/usr/bin/supervisord"]` (Starts a process supervisor)

### Dockerfile Best Practices 
1. Optimize for Build Speed (Layer Caching)
+ Docker builds images by executing each instruction in a Dockerfile sequentially, creating a new read-only layer for each step. Docker saves this layer and can reuse it in future builds (caching).
+ Principle: Place instructions that change infrequently near the top of the Dockerfile, and instructions that change frequently near the bottom.
+ Action: Your application code (COPY or ADD instruction) should be placed after environment setup and dependency installation. If your code changes, only the subsequent layers need to be rebuilt, saving time.

2. Minimize Image Size (Layer Reduction) 
+ Smaller images are faster to pull and deploy.
+ Combine RUN Commands: Use the && operator to chain multiple commands into a single RUN instruction. This reduces the number of layers created for installing dependencies.
+ Example: Instead of separate RUN apt-get update and RUN apt-get install, combine them.
+ Clean Up Immediately: In the same chained RUN command, clean up downloaded packages, caches, and temporary files (e.g., rm -rf /var/lib/apt/lists/* after installing packages). This ensures the temporary files are not stored in the final image layer.
+ Use Lean Base Images: Start your FROM instruction with the smallest possible base image (e.g., use Alpine versions, which are very small, or slim variants of official images).

3. Improve Security 
+ Security is paramount, especially when running containers in production.
+ Avoid Running as Root: By default, containers run as the root user. Use the USER instruction to switch to a less-privileged user after installing necessary system packages. This prevents potential attackers from gaining root access to the host system if the container is compromised.
+ Action: Create a dedicated user/group and switch to it:
+ Dockerfile
```
RUN groupadd -r appuser && useradd -r -g appuser appuser
USER appuser
```
Define `EXPOSE` Ports: While not a security measure itself (it's documentation), always explicitly define which ports the application uses with EXPOSE.

4. Use .dockerignore 
+ Create a file named .dockerignore in the same directory as your Dockerfile. This file lists files and directories that Docker should exclude when sending the build context to the Docker daemon.
+ Benefit: This dramatically speeds up the build process and results in smaller images by excluding unnecessary files like:
+ .git folders
+ node_modules (if you run npm install inside the container)
+ Local logs or test directories
+ .vscode or other IDE configuration folders

5. Use Specific Tags for Base Images 
+ Always specify an explicit tag for your FROM image, instead of just latest.
+ Action: Use FROM ubuntu:22.04 or FROM node:18-slim instead of FROM ubuntu or FROM node.
+ Benefit: This ensures your build is reproducible; you won't accidentally pull a new, incompatible version of the base image that could break your application during a future build.




