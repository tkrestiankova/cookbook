# Tuple

- ordered, immutable and usually consist of heterogeneous items (not enforced)
- (almost) everything we know about lists applies to tuples, but they can't be modified (immutability)
```python
t = ("warsaw", "barcelona", "new york")
t[3] = "los angeles"
>>> Traceback (most recent call last):
>>>    File "<stdin>", line 1, in <module>
>>> TypeError: 'tuple' object does not support item assignment
```

### Why would tuple insted of list?
- Program execution is faster when manipulating a tuple than it is for the equivalent list (This is probably not going to be noticeable when the list or tuple is small)
- You do not want data to be modified during the lifetime of the program

### How to create a tuple
- using `()` operators: t = ()
- value + trailing comma: t = "hello", 
- tuple packing: t = "hello", "world"
- using a constructor: t = tuple("hello")

```python
# be careful about creating tuples with 1 item (missing trailing coma will create a string)
this_is_string = ("hello")
print(type(this_is_string))
>>> <class 'str'>

this_is_tuple = ("hello",)
print(type(this_is_tuple))
>>> <class 'tuple'>
```

### Accessing values in tuple
- it is basically the same as with lists:
    - using positive/negative index
    ```python
    t = ("warsaw", "barcelona", "new york")
    print(t[0])
    >>> warsaw
    print(t[-1])
    >>> new york
    ```
    - slicing
    ```python
    print(t[:2])
    >>> ('warsaw', 'barcelona')
    ```

### Changing a tuple 
- we already know that tuples are immutable, which means that elements of a tuple cannot be changed. But, it the element is itself a muatble data type (eg. dict or list), its nested items can be changed
```python
t = ("i_am_immutable_string", {"i_am": "mutable_dictionary"})
t[0] = "world"
>>> Traceback (most recent call last):
>>>    File "<stdin>", line 1, in <module
>>> TypeError: 'tuple' object does not support item assignment
t[1].update({"i_am": "new_value"})
print(t)
>>> ('i_am_immutable_string', {'i_am': 'new_value'})
```
