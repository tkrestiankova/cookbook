# Dictionary

- indexed by keys (key can be any immutable data type)
- dictionaries are key:value pairs, where all keys must be unique
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