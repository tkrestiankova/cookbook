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

Every function is an object (like everything else in Python), but can an object be a function? No. However, we can do this:

```python
class Greeter:
    def __init__(self, name: str):
        self.name = name
    def __call__(self):
        print(f"Hello {self.name}")

greet = Greeter(name="Tami")
greet()  # call object like a function
```

this will return:

```shell
Hello Tami
```

## Types of Python functions

### Built-in functions
These are functions provided by the Python interpreter. They are available for use anytime, and there is no need for import.
Good examples, that we most likely use on a daily basis, might be constructors, `all()`, `any()`, `getattr()`, `hasattr()`, `isinstance()`, or `print()`

Here is the full list of Python built-in functions: https://docs.python.org/3/library/functions.html

### User-defined functions
These are designed by a developer. A function can perform any task and the goal is to reduce complexity of a program.

### Lambda functions
These are also known as anonymous functions or lambda expressions. Instead of `def` keyword, we create them with `lambda` keyword. Lambdas are not so common because their use is very restricted. It allows a single expression, the result of which is the return value. This means that no other language features, like multiple statements, conditionals, iteration or exception handling can be included.

```python
sum = lambda x, y: x + y

sum(2, 3)
```

### Closures and decorators
_"A decorator is a function that takes in a function and returns an augmented copy of that function. When writing closures and decorators, 
you must keep the scope of each function in mind. In Python, functions define scope. Closures have access to the scope of the function 
that returns them; the decorator's scope."_ ([source](https://towardsdatascience.com/decorators-and-closures-by-example-in-python-382758321164))

#### Closure

```python
def outer_function(name: str):
    def inner_function():
        print(f"I have access to outer's function scope. This is the name: {name}")
    return inner_function
    
i_hold_value = outer_function(name="Tamara")
i_hold_value()
```
as a result, this will print:
```shell
I have access to outer's function scope. This is the name: Tamara
```

#### Decorator

```python
def log(func):
    def _log(*args, **kwargs):
        print("Function start")
        func()
        print("Function done")
    return _log
    
@log
def foo():
    print("I am inside the function")

foo()
```

as a result, this will print:

```shell
Function start
I am inside the function
Function done
```

## Methods
Methods, unlike functions, are associated with the object/instance of the class they belong to. A method is called "on" an object and we cannot invoke it just by its name.

```python
def foo():
    print("I am a function")
    
class Test:
    def foo(self):
        print("I am a method")
        
# call a function
foo()

# call a method
test_obj = Test()
test_obj.foo()
```

### Static method
A difference between a method and a static method is that a static method is bound to the class itself, not an instance of the object. 
It means, that static method can be called without an object for that class.

```python
class Test:
    @staticmethod
    def foo():
        print("I am a static method")
        
Test.foo()  # no need for Test().foo()
```

### @property
A Python `@property` decorator is a pythonic way to use getters and setters in OOP. 
In Python, the `@property` decorator is a built-in function that allows us to define methods that can be accessed like an attribute.
This can be useful when we want to add some additional behavior to the getting or setting of an attribute, or when we want to define a 
method that is more readable and easier to use than a traditional method.

```python
class Person:
    def __init__(self, first_name: str, last_name: str):
        self.first_name = first_name
        self.last_name = last_name
    
    @property
    def full_name(self) -> str:
        return f"{self.first_name} {self.last_name}"
        
p = Person(first_name="John", last_name="Doe")
print(p.first_name)
print(p.last_name)
print(p.full_name)
```
this will return
```shell
John
Doe
John Doe
```

## Arguments

