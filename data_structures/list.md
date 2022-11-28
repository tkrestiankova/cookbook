# List
- it is a collection of arbitrary objects 
  - list items do not have to be homogeneous (of the same kind)
  - they can contain duplicates
  - they can be nested
  ```python
  i_contain_different_datatypes = [1, "hello", ("i am", "tuple"), {"a": "A"}, True]
  i_am_nested = [["hello", "world"], 1, "hola"]
  i_ontain_duplicates = ["a", "a", "a"]
  ```
- we access values by indexes (int) and we can use slicing
```python
# let's access values by indexes
l = ["hello", "world"]
print(l[0])
>>> hello
print(l[1])
>>> world

# we can also use negative index (it counts from the end of the list)
print(l[-1])
>>> world
print(l[-2])
>>> hello

# for slicing, let's create a longer list
l = ["h", "e", "l", "l", "o", "w", "o", "r", "l", "d"]
print(l[0:5])
>>> ['h', 'e', 'l', 'l', 'o']
print(l[5:10])
>>> ['w', 'o', 'r', 'l', 'd']
```
- they are mutable and ordered

```python
# Let's prove lists are ordered

# first we create two dictionaries (unordered data structure)
d1 = {"a": "A", "b": "B"}
d2 = {"b": "B", "a": "A"}
print(d1==d2)
>>> True

# now, let's create two lists
l1 = ["hello", "world"]
l2 = ["world", "hello"]
print(l1==l2)
>>> False

# Now let's prove lists are mutable
l1 = ["hello"]
print(id(l1))
>>> 4501758976
l1.append("world")
print(id(l1))
>>> 4501758976
```

### Creating a list
- using a pair of square brackets to denote the empty list: `l = []`
- using square brackets, separating items with commas: `l = ["hello", "world"]`
- using a list comprehension: `l = [x for x in range(5)]`
- using the constructor `list()` or `list(iterable)`: l = list() || l = list(range(5))
