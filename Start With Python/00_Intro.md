### Python Programming 
Key Concepts:
+ The Trap of Mutable Defaults: In Python, default arguments are evaluated once at definition time, not every time the function is called. If you use a mutable object (like a list or dict) as a default, that same object is shared across all function calls.
+ Safe Dictionary Access: Using .get() is the industry standard for accessing keys that might not exist, allowing for a fallback value without crashing the program with a KeyError.
+ Argument Packing: *args and **kwargs allow functions to accept any number of arguments. *args collects extra positional arguments into a tuple, while **kwargs collects keyword arguments into a dictionary.
+ The LEGB Hierarchy: This is the specific order Python uses to search for a variable name: Local, then Enclosing (non-local), then Global, and finally Built-in.
Vocabulary List:
Mutable: An object whose state can be modified after it is created (e.g., list, dict, set).
Immutable: An object whose state cannot be changed after creation (e.g., int, str, tuple).
Syntactic Sugar: Syntax within a programming language that is designed to make things easier to read or to express, such as the @decorator syntax.
Generator: An iterator that yields items one at a time, allowing for extreme memory efficiency compared to lists.
Deep Copy: A process that creates a new compound object and then, recursively, inserts copies into it of the objects found in the original.
Key Questions:
Why is def func(val, items=None): preferred over def func(val, items=[]):?
What is the difference between a tuple and a list in the context of *args?
How does the E in LEGB apply to nested functions (closures)?
How do you stop a terminal from opening the Microsoft Store when trying to run the python command?
When should you use is instead of ==? (Hint: Think about None checks).

1. Why items=None is preferred over items=[]
In Python, default arguments are evaluated only once—at the moment the function is defined.

If you use items=[], that specific list object is created once and stored in the function's __defaults__ attribute.

Every subsequent call to the function that doesn't provide an items argument will share that exact same list.

Using items=None and then checking if items is None: items = [] inside the function body ensures a new list is created every single time the function is called.

2. *args: Tuple vs. List
When you use *args in a function signature, Python packs the extra positional arguments into a tuple, not a list.

Immutability: Since it's a tuple, the arguments passed are protected from being modified within the args collection itself (though the objects inside could still be mutable).

Performance: Tuples are slightly more memory-efficient and faster to iterate over than lists.

3. The "E" (Enclosing) in LEGB and Closures
The Enclosing scope refers to the local scope of any enclosing functions. This is the heart of closures.

If you have a nested_func inside an outer_func, the nested_func can see and use variables defined in outer_func.

Those variables are neither "Global" nor "Local" to the nested function; they are in the Enclosing scope.

This allows the nested function to "remember" the state of the outer function even after the outer function has finished executing.

4. Stopping the Microsoft Store Redirect
This is a Windows-specific behavior where "App Execution Aliases" take over when Python isn't found.

Open Settings > Apps > Advanced app settings > App execution aliases.

Find python.exe and python3.exe.

Toggle them to Off.

Ensure your actual Python installation path is added to your system's Environment Variables (Path).

5. is vs ==
== checks for Equality: Do these two objects have the same value?

is checks for Identity: Are these two variables pointing to the exact same memory address?

Best Practice: You should almost always use is when comparing against None (e.g., if val is None:). This is because None is a singleton in Python (there is only ever one None object in memory), and is is faster and safer than == which could be overridden by a class's __eq__ method.
