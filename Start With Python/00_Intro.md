### Python Programming 
#### 1. Key Concepts:
+ The Trap of Mutable Defaults: In Python, default arguments are evaluated once at definition time, not every time the function is called. If you use a mutable object (like a list or dict) as a default, that same object is shared across all function calls.
+ Safe Dictionary Access: Using .get() is the industry standard for accessing keys that might not exist, allowing for a fallback value without crashing the program with a KeyError.
+ Argument Packing: *args and **kwargs allow functions to accept any number of arguments. *args collects extra positional arguments into a tuple, while **kwargs collects keyword arguments into a dictionary.
+ The LEGB Hierarchy: This is the specific order Python uses to search for a variable name: Local, then Enclosing (non-local), then Global, and finally Built-in.

#### 2. Vocabulary List:
+ Mutable: An object whose state can be modified after it is created (e.g., list, dict, set).
+ Immutable: An object whose state cannot be changed after creation (e.g., int, str, tuple).
+ Syntactic Sugar: Syntax within a programming language that is designed to make things easier to read or to express, such as the @decorator syntax.
+ Generator: An iterator that yields items one at a time, allowing for extreme memory efficiency compared to lists.
+ Deep Copy: A process that creates a new compound object and then, recursively, inserts copies into it of the objects found in the original.

### Key Questions:
1. Why is def func(val, items=None): preferred over def func(val, items=[]):?
+ In Python, default arguments are evaluated only once—at the moment the function is defined.
+ If you use items=[], that specific list object is created once and stored in the function's __defaults__ attribute.
+ Every subsequent call to the function that doesn't provide an items argument will share that exact same list.
+ Using items=None and then checking if items is None: items = [] inside the function body ensures a new list is created every single time the function is called.

2. What is the difference between a tuple and a list in the context of *args?
+ When you use *args in a function signature, Python packs the extra positional arguments into a tuple, not a list.
+ Immutability: Since it's a tuple, the arguments passed are protected from being modified within the args collection itself (though the objects inside could still be mutable).
+ Performance: Tuples are slightly more memory-efficient and faster to iterate over than lists.
3. How does the E in LEGB apply to nested functions (closures)?
+ The Enclosing scope refers to the local scope of any enclosing functions. This is the heart of closures.
+ If you have a nested_func inside an outer_func, the nested_func can see and use variables defined in outer_func.
+ Those variables are neither "Global" nor "Local" to the nested function; they are in the Enclosing scope.
+ This allows the nested function to "remember" the state of the outer function even after the outer function has finished executing.
4. How do you stop a terminal from opening the Microsoft Store when trying to run the python command?
+ This is a Windows-specific behavior where "App Execution Aliases" take over when Python isn't found.
+ Open Settings > Apps > Advanced app settings > App execution aliases.
+ Find python.exe and python3.exe.
+ Toggle them to Off.
+ Ensure your actual Python installation path is added to your system's Environment Variables (Path).
5. When should you use is instead of ==? (Hint: Think about None checks).
+ == checks for Equality: Do these two objects have the same value?
+ is checks for Identity: Are these two variables pointing to the exact same memory address?
+ **Best Practice:** You should almost always use is when comparing against None (e.g., if val is None:). This is because None is a singleton in Python (there is only ever one None object in memory), and is is faster and safer than == which could be overridden by a class's __eq__ method.

#### 4. Advanced Memory & Performance
+ **Interning**: Python automatically "interns" small integers (usually -5 to 256) and certain strings to save memory. This is why a = 10; b = 10; a is b is True, but a = 500; b = 500; a is b might be False.

+ **Slots (__slots__)**: In classes with thousands of instances, use __slots__ = ('name', 'age'). This prevents the creation of a __dict__ for each instance, drastically reducing RAM usage.

GIL (Global Interpreter Lock): A mutex that allows only one thread to execute Python bytecode at a time.

Use Threading for I/O-bound tasks (API calls, file reading).

Use Multiprocessing for CPU-bound tasks (Data processing, image manipulation).

2. The "Dunder" (Double Under) Methods

These allow your objects to mimic built-in types:

__str__ vs __repr__: str is for end-users (pretty); repr is for developers (debugging, should ideally look like the code used to create the object).

__call__: Allows an instance of a class to be called like a function.

__getitem__ / __setitem__: Allows your object to use square bracket notation obj[key].

__enter__ / __exit__: Used to create custom Context Managers (the with statement).

3. Functional Programming Tools

Lambda Functions: Anonymous, one-line functions. add = lambda x, y: x + y.

Map/Filter: * map(func, iterable): Applies function to all items.

filter(func, iterable): Keeps items where function returns True.

Functools.lru_cache: A decorator that automatically caches the results of a function based on its arguments. Great for optimizing recursive math functions.

4. Code Quality & Standards

Type Hinting: Use the typing module to make code readable and catch errors before runtime.

def process_data(name: str, age: int) -> bool:
    return True


PEP 8: The official style guide. Key takeaways:

4 spaces per indentation level.

Variable/Function names: snake_case.

Class names: PascalCase.

Constants: UPPER_SNAKE_CASE.

The Zen of Python: Type import this in any Python terminal to see the 19 guiding principles of the language (e.g., "Beautiful is better than ugly").

5. Dataclasses (Python 3.7+)

Instead of writing a long __init__ method, use the @dataclass decorator:

from dataclasses import dataclass

@dataclass
class User:
    id: int
    username: str
    email: str


It automatically generates __init__, __repr__, and __eq__ for you.

6. Common Library Roles

os / pathlib: Handling file paths (prefer pathlib for modern code).

itertools: Functions for efficient looping (e.g., chain, cycle, product).

collections: Special data structures like defaultdict, Counter, and namedtuple.

json: Parsing and creating JSON data.
