### **Project Startup**
#### **Prerequisites**

+ Before you begin, ensure you have the following prerequisites:

- Python installed on your system
- Pip or uv or any other(Python package manager) installed
- Basic understanding of virtual environments (optional but recommended)

### **Setup Instructions**

### **Mac/Linux**
1. Create a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate
    # deactivate  -- to deactivate an environment.
    ```

2. Install FastAPI and Uvicorn:
    ```bash
    pip install fastapi uvicorn
    pip install "uvicorn[standard]"
    ```

### **Windows**
1. Create a virtual environment:
    ```bash
    python -m venv venv
    venv\Scripts\activate
    ```

2. Install FastAPI and Uvicorn:
    ```bash
    pip install fastapi uvicorn
    pip install "uvicorn[standard]"
    ```
### main.py
from fastapi import FastAPI
```
Jargon: Dependency Injection, Class Instantiation, ASGI Framework.

The Explanation: importing the FastAPI class from fastapi module, which is the primary entry point for the application.
Unlike Flask (which is WSGI-based(web server Gateway Interface), FastAPI is an ASGI (Asynchronous Server Gateway Interface) framework.
This allows it to handle asynchronous requests natively, making it one of the highest-performing Python frameworks available today.
```
app = FastAPI()
```
Jargon: Application Instance, Singleton Pattern, Router Registration.

The Explanation: "I am instantiating the FastAPI class to create the app object.
This object acts as the central hub for the application. It handles the Request-Response cycle,
manages state, and serves as the registry for all route operations and middleware.
```

@app.get("/hello")
+ The Jargon: JSON Serialization, Data Marshalling, Pydantic Integration.
+ The Explanation: "FastAPI automatically handles Data Marshalling.
  It takes this Python dictionary and serializes it into a JSON-formatted response body.
  One of the major advantages here is that FastAPI manages the Content-Type headers automatically,
  ensuring the client receives the data as application/json without manual intervention.

+ OpenAPI Integration: Mention that by simply writing this code,
  FastAPI automatically generates interactive documentation at /docs (Swagger UI) and /redoc.
+ Performance: Note that FastAPI's performance is on par with NodeJS and Go because of its underlying Starlette engine.
+ Type Safety: Emphasize that while this example is simple, using type hints in the function
  signature allows FastAPI to perform automatic request validation.

# Technical Note: Python Execution Context & `__name__`

## 1. The Concept of "Dunder" Name
Every Python module has a built-in attribute called `__name__`. This attribute acts as a "Self-Identification" mechanism for the code.

## 2. Execution Modes

### Mode A: Direct Execution
When you run a file directly: `python my_script.py`
- The Python Interpreter sets `__name__ = "__main__"`.
- **Result:** The code inside the `if` block **runs**.

### Mode B: Import as Module
When you import the file: `import my_script` (inside `other_file.py`)
- The Python Interpreter sets `__name__ = "my_script"`.
- **Result:** The code inside the `if` block **is ignored**.



## 3. Best Practices (Interview Highlights)

* **Avoid Global Logic:** Never write heavy processing logic at the top level of a script. Always wrap it in a function (usually `main()`).
* **Boilerplate Protection:** Using this block protects against **Namespace Pollution**. It ensures that importing a utility file doesn't accidentally start a web server or a database migration.
* **Unit Testing:** This pattern is essential for testing. Test runners (like `pytest`) import your modules to test functions; if you don't use this block, your entire app might start running during the test suite.


# **UVicorn Command Reference**

This reference guide provides information about the `uvicorn` command and its usage.

- **Command:**
    ```bash
    uvicorn app.main:app --reload
    ```

    This command is used to run a FastAPI application using the UVicorn ASGI server with auto-reload enabled.

    **Arguments:**
    - `app.main:app`: Specifies the Python module and ASGI application instance to run. In this example, `app` refers to the FastAPI application instance within the `main` module.
    - `--reload`: Enables auto-reload functionality, causing the server to restart whenever the source code changes.

    **Usage:**
    - Run the command in the terminal to start the FastAPI application with UVicorn and auto-reload functionality.
