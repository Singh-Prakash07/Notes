The 4 Pillars of FastAPI
#### 1. Native Asynchronous Support (ASGI)
+ Unlike traditional frameworks like Flask or Django (which are WSGI-based), FastAPI is an ASGI
(Asynchronous Server Gateway Interface) framework.
+ The Jargon: It supports Concurrency and Non-blocking I/O via Python's async and await keywords.
  This allows the server to handle thousands of concurrent requests without waiting for one to finish
  before starting the next.

#### 2. Robust Data Validation with Pydantic
+ FastAPI uses Pydantic as its data-parsing engine.
+ The Jargon: It performs Automatic Data Marshalling and validation. When a request hits an endpoint,
  FastAPI validates the payload against your defined schemas. If the data is malformed,
  it automatically returns a structured 422 Unprocessable Entity error, saving you from writing
  manual "if-else" validation checks.
#### 3. Standard-Based Documentation (OpenAPI)
+ FastAPI is built on open standards: OpenAPI (formerly Swagger) and JSON Schema.
+ The Benefit: It provides "Documentation as Code." The moment you define an endpoint,
  FastAPI automatically generates an interactive Swagger UI (at /docs) and ReDoc (at /redoc).
  This significantly improves the developer experience (DX) and frontend-backend handoff.
#### 4. Type Safety and Dependency Injection
+ By leveraging Python Type Hints, FastAPI provides excellent autocompletion and error checking during development.
+ The Jargon: It features a powerful Dependency Injection (DI) system.
  This allows for modularity, making it easy to "inject" database sessions, authentication logic,
  or security protocols into your path operations without creating tightly coupled code.
## Core Components
* **Starlette:** The underlying toolkit for web routing, WebSockets, and GraphQL support.
* **Pydantic:** The data validation layer that ensures type safety.
* **Uvicorn:** The lightning-fast ASGI server used to run the application.

# The Foundations of FastAPI: Starlette & Pydantic

## 1. Starlette (The Web Toolkit)
Starlette provides the underlying web infrastructure for FastAPI. It is a production-ready ASGI toolkit.

### Key Features:
* **High Performance:** On par with Node.js and Go.
* **WebSocket Support:** Native support for real-time, two-way communication.
* **GraphQL Support:** Easily integrated for modern data fetching.
* **Background Tasks:** Allows you to trigger logic (like sending an email) after a response is sent, without making the user wait.
* **Middleware Support:** Handles CORS, GZip compression, and Authentication at the transport layer.

---

## 2. Pydantic (The Data Engine)
Pydantic is the most widely used data validation library in the Python ecosystem. It uses Python 3.6+ type hints to define data structures.

### Key Features:
* **Data Parsing:** It doesn't just validate; it "parses" data into Python objects. If you send a string `"10"`, Pydantic can convert it to the integer `10` automatically if that's what you defined.
* **Strict Validation:** It ensures that the "Shape" of the data entering your application is exactly what you expect.
* **Serialization:** Effortlessly converts complex Python objects (like Database models) back into JSON for the client.
* **Clear Error Messages:** When validation fails, it provides the exact location (field) and reason for the failure in a JSON format.

---

## 3. The "FastAPI" Synergy
FastAPI takes these two and adds several "quality of life" features:

| Feature | Provided By | FastAPI's Addition |
| :--- | :--- | :--- |
| **Routing** | Starlette | Automatic OpenAPI (Swagger) tags based on routes. |
| **Request Data** | Pydantic | Automatic conversion of request bodies into Pydantic models. |
| **Dependencies** | FastAPI | A unique "Dependency Injection" system to link the two. |

### Interview Summary
If asked, "Why not just use Starlette?"
**Answer:** "While Starlette provides the high-performance ASGI core, using it alone requires writing manual data validation and documentation logic. FastAPI automates the validation (via Pydantic) and the documentation (via OpenAPI), allowing for faster, safer development."
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
