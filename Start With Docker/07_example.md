### 1. create a image
+ creating an image of python:3.12-slim-bookworm with uv installed in it.
  1. Create a file in your directory and name it exactly python_with_uv (no file extension). Paste this code inside it:
     ```
      FROM python:3.12-slim-bookworm
      # Copy the uv binaries straight from Astral's official release into this image
      COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/
     ```
  2. Before we can push anything to Docker Hub, you need to authenticate your terminal using ` docker login`
     ```
      docker build -f python_with_uv -t yourusername/python_with_uv:3.12-slim .
     ```
     + -f python_with_uv: Tells Docker to read your custom-named file.
     + -t yourusername/python_with_uv:3.12-slim: Names the image and gives it a clear version tag (3.12-slim).
     + .: Sets the current directory as the build context.
  3. Now that the image is built and tagged correctly, push it to the cloud using `docker push yourusername/python_with_uv:3.12-slim`
  4. if we have created an application and want to create an image of our project using this image
  5. Start directly from your newly created cloud image!
```
# Start directly from your newly created cloud image!
FROM yourusername/python_with_uv:3.12-slim
WORKDIR /app
COPY uv.lock pyproject.toml /app/
RUN uv sync --frozen --no-install-project --no-dev
COPY . /app
CMD ["uv", "run", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```
### 2. create a project using image
  #### method 1
    + we can spin up our image in an interactive "sandbox" mode. This allows you to run uv commands inside the container to generate your pyproject.toml, uv.lock, and main.py files directly onto your local computer.
    + `docker run --rm -it -v .:/app yourusername/python_with_uv:3.12-slim bash`
    + -v .:/app: Mounts your empty local folder into the container's /app folder. Anything created inside the container will instantly appear on your real computer.
    + bash: Overrides the default startup and drops you into a terminal terminal inside the container.
    ```
    # Initialize a new project structure
    uv init --app
    
    # Add FastAPI and Uvicorn dependencies
    uv add fastapi uvicorn
    ```
    + Type exit to leave. Look at your local folder—your pyproject.toml, uv.lock, and a sample app are fully generated and ready!
