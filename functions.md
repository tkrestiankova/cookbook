## What is a function

In programming, a function is a reusable block of code that executes a certain functionality when it is called. 
We can pass parameters to the function and return values from the function.

A very basic function example would be this:

```python
from typing import List

def welcome_message(name: str) -> str:
  return f"Dear {name}, welcome to Python seminar!"
```

To create a function, we use a `def` keyword.

TODO:
- type of functions ()
- arguments (limits, 256 until Python 3.7, no limit after that; type of arguments)
- lambda expressions
- closures / decorators
