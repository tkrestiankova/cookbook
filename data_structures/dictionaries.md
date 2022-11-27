# Dictionary

- indexed by keys (key can be any immutable data type)
- dictionaries are key:value pairs, where all keys must be unique
- they are unordered and mutable objects
  - *A mutable object is an object whose state can be modified after it is defined*

```python
example_dict = {
    "key_1": "value_1",
    "key_2": "value_2",
    "key_3": "value_3"
}

# id(obj) gets a memory address of an object `obj`
print(id(example_dict))
>>> 4499428352

# Let;s change the state of the `example_dict` and check the memory address again
example_dict.update({"key_x": "value_x"})
print(id(example_dict))
>>> 4499428352  # THE SAME ADDRESS

# Now let's have a look at an immutable object, such as string
my_str = "Hello"
print(id(my_str))
>>> 4502273456

# Now we modify the state of `my_str` and check the memory address again
my_str = "Hello world"
print(id(my_str))
>>> 4502273072  # A NEW ADDRESS

```

- most common operations are:
  - **storing** a value with a key
  - **extracting** the value given the key
  - **deleting** a key:value pair using `del`
- extracting a value using non-existin key raises `KeyError`
  - To avoid `KeyError` we can use `.get(key)` method that returns `None` if the key:value pair does not exist

```python
example_dict = {
    "key_1": "value_1",
    "key_2": "value_2",
    "key_3": "value_3"
}

# Extract value using an existing key "key_1"
extracted_value = example_dict["key_1"]
print(extracted_value)
>>> value_1

# Extract value using non-existing key "key_x"
extracted_value = example_dict["key_x"]
print(extracted_value)
>>> Traceback (most recent call last):
>>>    File "<stdin>", line 1, in <module>
>>> KeyError: 'key_x'

# To avoid KeyError exception, we can use `.get(key)` method
extracted_value_1 = example_dict.get("key_1")
extracted value_2 = example_dict.get("key_x")
print(extracted_value_1)
print(extracted_value_2)
>>> value_1
>>> None
```

There are more ways to create a dictionary:

- Using a `dict()` constructor -> builds a dictionary from any sequence of key:value pairs

```python
# create a dictionary from a list of tuples
example_list_of_tuples = [
    ("key_1", "value_1"),
    ("key_2", "value_2"),
    ("key_3", "value_3")
]
list_of_tuples_to_dict = dict(example_list_of_tuples)
>>> {"key_1": "value_1", "key_2": "value_2", "key_3": "value_3"}

# In case keys are simple strings, we can specify pairs use keyword arguments
dict_from_keyword_args = dict(
    key_1="value_1",
    key_2="value_2",
    key_3="value_3"
)
print(dict_from_keyword_args)
>>> {"key_1": "value_1", "key_2": "value_2", "key_3": "value_3"}

# We can even mix these approaches
dict_from_dict_and_keyword_args = dict(
    {"key_1": "value_1", "key_2": "value_2"},
    key_3="value_3"
)
print(dict_from_dict_and_keyword_args)
>>> {"key_1": "value_1", "key_2": "value_2", "key_3": "value_3"}

# Using the constructor with no value creates an empty dictionary
empty_dict = dict()
print(empty_dict)
>>> {}
```

- using the for loop

```python
my_dict = dict()
keys = ["key_1", "key_2", "key_3"]
values = ["value_1", "value_2", "value_3"]
for key in keys:
    for value in values:
        my_dict.update({key: value})
print(my_dict)
>>> {"key_1": "value_1", "key_2": "value_2", "key_3": "value_3"}

# Optionally, we can use `.zip()` over those sequences
my_dict = dict()
for key, value in zip(keys, values):
    my_dict.update({key: value})
print(my_dict)
>>> {"key_1": "value_1", "key_2": "value_2", "key_3": "value_3"}
```

## Operations

We'll be using the `example_dict` to demonstrate the operations

```python
example_dict = {"key": "value"}
```

- check if a key exists in a dictionary

```python
example_dict = {"key": "value"}
"key" in example_dict
>>> True
"key_x" in example_dict
>>> False
```

- print keys, values or items

  ```python
  example_dict.items()
  >>> dict_items([('key', 'value')])
  example_dict.keys()
  >>> dict_keys(['key'])
  example_dict.values()
  >>> dict_values(['value'])
  ```
- copy a dictionary (make a shallow copy)

  - This is a very useful feature, because dicts are mutable

  ```python
  id(example_dict)
  >>> 4499428352
  copy_of_example = example_dict.copy()
  id(copy_of_example)
  >>> 4502470336
  ```
- return and delete a value or both key and value

  ```python
  # if we want to return the value and delete key:value pair, we use .pop()
  example_dict.pop("key")
  >>> "value"
  example_dict.pop("key")
  >>> Traceback (most recent call last):
  >>>  File "<stdin>", line 1, in <module>
  >>> KeyError: 'key'

  # if we want to return both key and value and then delete the pair, we use .popitem()
  # items are returned in LIFO order
  example_dict.popitem()
  >>> ('key', 'value')
  ```
- update (probably the most common operation)

  ```python
  new_dict = {"key_x": "value_x"}
  example_dict.update(new_dict)
  print(example_dict)
  >>> {"key": "value", "key_x": "value_x"}

  # Let's demonstrate that the order is important
  dict_a = {"key": "a"}
  dict_b = {"key": "b"}

  dict_a.update(dict_b)
  print(dict_a)
  >>> {"key": "b"}

  # But if we did 
  dict_b.update(dict_a)
  print(dict_b)
  >>> {"key": "a"}
  ```
