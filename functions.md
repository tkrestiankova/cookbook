## What is a function

In programming, a function is a **reusable** block of code (DRY principle!) that executes a certain functionality when it is called. 
We can pass parameters to the function and return values from the function. 

A very basic function example would be this:

```python
from typing import List

def welcome_message(name: str) -> str:
  return f"Dear {name}, welcome to Python seminar!"
```

To create a function, we use a `def` keyword. If no `return` statement is present in the function body, the function returns `None`.

## Types of Python functions

### Built-in functions
These are functions provided by the Python interpreter. They are available for use anytime, and there is no need for import.
Good examples, that we most likely use on a daily basis, might be constructors, `all()`, `any()`, `getattr()`, `hasattr()`, `isinstance()`, or `print()`

Here is the full list of Python built-in functions: https://docs.python.org/3/library/functions.html

### User-defined functions

### Lambda functions

### Closures and decorators

### Recursion functions



TODO:
- type of functions ()
- arguments (limits, 256 until Python 3.7, no limit after that; type of arguments)
- lambda expressions
- closures / decorators
