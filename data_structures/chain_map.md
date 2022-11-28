# ChainMap

- helps to manage multiple dictionaries as one
- _"`ChainMap` groups multiple dictionaries and mappings in a single, updatable view with dictionary-like behavior"_
- It can contain repeated keys with different values
  - When you search for a key, you get the first occurrence of the target key (so the order is important)
 
```python
from collections import ChainMap

d1 = {"a": "A_from_d1"}
d2 = {"a": "A_from_d2"}
d3 = {"b": "B", "c": "C", "d": "D"}

chain_map = ChainMap(d1, d2, d3)
print(chain_map)
>>> ChainMap({'a': 'A_from_d1'}, {'a': 'A_from_d2'}, {'b': 'B', 'c': 'C', 'd': 'D'})

# let's lookup "a" key
print(chain_map["a"])
>>> A_from_d1

# now, if we changed the order
chain_map = ChainMap(d2, d1, d3)
print(chain_map["a"])
>>> A_from_d2
```
