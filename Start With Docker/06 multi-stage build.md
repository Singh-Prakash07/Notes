### Multi-Stage Builds
+ Multi-stage builds allow you to use multiple `FROM` statements in a single Dockerfile. Each `FROM` statement begins a new stage of the build.
+ **Core Principle**: You use one stage to build the application (where large tools, compilers, and dependencies are needed) and a subsequent stage to create the final production image, copying only the necessary build artifacts (the compiled binary, static files, etc.) from the previous stage.
+ Benefit: This drastically reduces the final image size because the heavy build dependencies are left behind in the temporary build stages.
#### Key Instructions and Syntax
1. Naming Stages (AS)
+ You can name a build stage using the AS <name> syntax after the FROM instruction. This allows you to reference it later.
+ Syntax: `FROM <base_image> AS <stage_name>`
+ Example: `FROM node:20 AS build-stage`

2. Copying from a Previous Stage (--from)
+ The COPY instruction is used with the --from flag to pull artifacts from a named stage.
+ Syntax: `COPY --from=<stage_name> <source> <destination>`
+ Example: Building a Node.js Application

+ This example shows how to build a Node.js application (which creates many temporary files in node_modules) while ensuring the final image is clean and small.
+ Stage 1: The Build Stage (The "Builder")
+This stage contains everything needed to compile and package the application.
+ Dockerfile
```
# Stage 1: Build Stage (large base image and build tools)
FROM node:20 AS builder

WORKDIR /app
COPY package*.json ./
RUN npm install          # Install all dependencies (dev and prod)

COPY . .
RUN npm run build        # Run the build process (e.g., compile code)
Stage 2: The Final Stage (The "Runtime")
This stage uses a lightweight base image and copies only what's necessary for runtime from the builder stage.
```
+ Dockerfile
```
# Stage 2: Production Stage (minimal base image)
FROM node:20-slim

WORKDIR /app
# 1. Copy only production dependencies from the node_modules folder in the 'builder' stage
COPY --from=builder /app/node_modules ./node_modules

# 2. Copy the compiled code/static assets
COPY --from=builder /app/dist ./dist

# Set the command to run the application
CMD ["node", "dist/server.js"]
```
+ Result
+ Stage	Image Used	Dependencies Included	Final Image Size
+ Builder Stage	node:20	All build tools, compilers, source code, and development files (Very Large)	Not the final image
+ Final Stage	node:20-slim	Only necessary runtime files and production dependencies	Significantly Smaller
+ This process prevents the build artifacts and temporary files created in the builder stage from being included in your final deployable image.
