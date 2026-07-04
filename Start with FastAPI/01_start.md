### FastAPI
+ FastAPI is a modern, fast (high-performance), web framework for building APIs with Python based on standard Python type hints.
+ FastAPI stands on the shoulders of giants:
  1. Starlette for the web parts.
  2. Pydantic for the data parts.
+ To create a project either we use pip or we install uv using pip and then we use pip for all package installation.
+ We will use both pip and uv here to create FastAPI app.
  1. pip
     1. First we create virtual environement using python -m venv venv_name
     2. To activate env we use source venv_name/bin/activate, we use deactivate to deactivate
  2. uv
     1. we use ` uv init .` or ` uv init project_name`.
     2. next command ` uv add fastapi uvicorn`.
