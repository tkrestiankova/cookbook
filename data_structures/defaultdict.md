# Defaultdict

- from `collections` module
- subclass of a `dict` object 
- the main advantage is that `defaultdict` never raises `KeyError`
    - it provides a default value for a key that does not exists
    ```python
    from collections import defaultdict
    
    d = defaultdict(list)
    print(d)
    >>> defaultdict(<class 'list'>, {})
    print(d["non_existing_key"])
    >>> []
    ```

### Inner Working of defaultdict
Defaultdict adds one writable instance variable and one method in addition to the standard dictionary operations. The instance variable is the `default_factory` parameter and the method provided is `__missing__`.

- `default_factory` - the default value for the dictionary defined
- `__missing__()` - this function is used to provide the default value for the dictionary. It takes `default_factory` as an argument and it provides a default value for the given key. This method is basically called by the `__getitem__()` method of the `dict` class when the requested key is not found.

```python
d = defaultdict(list)
print(d.default_factory)
>>> <class 'list'>

d["names"] = ["john", "peter", "sam"]
d["cities"] = ["warsaw", "barcelona", "honolulu"]
print(d["names"])
>>> ["john", "peter", "sam"]
print(d["cities"])
>>> ["warsaw", "barcelona", "honolulu"]
print(d["non_existing_key"])
>>> []
```

