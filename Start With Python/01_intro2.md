#### 1. The Execution Model
  + Python is often called an interpreted language, but it actually follows a two-step execution process.Compilation:
    1. The source code (.py) is compiled into Bytecode (.pyc). Bytecode is a low-level, platform-independent set of instructions.
    2. Interpretation: The Python Virtual Machine (PVM) interprets the bytecode. This is where the code actually runs.
  + **Interview Tip**: If asked about .pyc files, explain they are cached bytecode stored in the __pycache__ folder to speed up subsequent executions by skipping the compilation step.

#### 2. Memory Management: Stack vs. Heap
  + where data lives.Everything in Python is an object. Even a simple integer like x = 10 creates an object on the Heap, while the name x on the Stack merely holds a reference (memory address) to that object.

#### 3. The Garbage Collector (GC)
   + Python uses two primary mechanisms to manage memory automatically:
     A. **Reference Counting (Primary)**
       + Every object has an ob_refcnt. When you assign an object to a new name or add it to a list, the count increases. When a name goes out of scope or is deleted (del), the count decreases.
       + `When count == 0: The memory is immediately deallocated`.
     B. **Generational Garbage Collection (Secondary)**
      + Reference counting fails at Reference Cycles (e.g., Object A points to B, and B points to A). To solve this, Python uses a generational GC.
      + **Generations**: Objects are categorized into Gen 0, Gen 1, and Gen 2.
      + **Survival**: New objects start in Gen 0. If they survive a GC cycle, they move to Gen 1, then Gen 2.
      + **Thresholds**: GC runs more frequently on younger generations (Gen 0) because most objects "die young."
#### 4. The Global Interpreter Lock (GIL)
   + The GIL is a mutex that allows only one thread to execute Python bytecode at a time.
   + **Why it exists**: To make CPython's memory management (reference counting) thread-safe without complex locking.
   + **Impact on Multi-threading**: It makes multi-threading ineffective for CPU-bound tasks (like heavy math).
   + **Workaround**: Use the multiprocessing module (which spawns separate interpreters with their own GIL) or use libraries like NumPy that release the GIL during C-extensions.
   + **2026 Context (PEP 703)**: Note that Python is moving toward an optional "No-GIL" build to allow better multi-core utilization.
#### 5. Memory Optimizations: Interning
  + Python "interns" certain objects to save memory and time:
    + **Small Integers**: Integers from $-5$ to $256$ are pre-allocated and cached.
    + **String Interning**: Short strings and identifiers are often interned so that a is b returns True if they have the same content.
