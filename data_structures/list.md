# List
- it is a collection of arbitrary objects 
  - list items do not have to be homogeneous (of the same kind)
  - it can contain duplicates
  - it can be nested
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
- it is mutable and ordered

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

### Most common operations
- lists support all [common sequence operations](https://docs.python.org/3/library/stdtypes.html?highlight=list#common-sequence-operations)
  - examples: `in`, `not in`, `+`, `*`, `len()`, `min()`, `max()`, `count()`
- lists support all [mutable sequence operations](https://docs.python.org/3/library/stdtypes.html?highlight=list#mutable-sequence-types)
  - examples: `del`, `append()`, `clear()` , `copy()`, `extend()`, `pop()`, `insert()`, `remove()`, `reverse()`  
  ```python
  # the difference between append and extend
  l1 = ["breaking", "bad"]
  l2 = ["is", "the", "best"]
  l1.append(l2)
  print(l1)
  >>> ['breaking', 'bad', ['is', 'the', 'best']]
  
  l1 = ["breaking", "bad"]
  l2 = ["is", "the", "best"]
  l1.extend(l2)
  print(l1)
  >>> ['breaking', 'bad', 'is', 'the', 'best']
  ```
- other than that, they add `sort()` method
  - this method sorts list in place and accepts 2 keyword arguments: `key` and `reverse`

Let's have a better look on how sorting works
```python
# this is built-on (ascending order)
l = [2, 7, 5]
l.sort()
print(l)
>>> [2, 5, 7]
l = ["h", "a", "c"]
l.sort()
print(l)
>>> ["a", "c", "h"]
```
- key parameter sets the built-in or custom function to compare each element of a list and sort it
```python
cities = ["Warsaw", "Barcelona", "New York", "Los Angeles", "Medellin"]

# using built-in sort
cities.sort()
print(cities)
>>> ['Barcelona', 'Los Angeles', 'Medellin', 'New York', 'Warsaw']

# using `len` as a custom sorting function "sort by item length"
cities.sort(key=len)
print(cities)
>>> ['Warsaw', 'New York', 'Medellin', 'Barcelona', 'Los Angeles']
```
The sort function will not work with custom classes. For custom classes, we need to use `lambda` function as a `key` parameter.
Why? Because sorting is basically just `<` comparison operation between items, and `<` operator cannot compare objects.
```
class Dog:
    def __init__(self, name: str, breed: str, age: int):
        self.name = name
        self.breed = breed
        self.age = age

leon = Dog(name="Leon", breed="Jack russell terrier", age=2)
ema = Dog(name="Ema", breed="Flat coated retriever", age=1)
gina = Dog(name="Gina", breed="American Staffordshire Terrier", age=12)

dog_list = [leon, ema, gina]

# now we want to sort these dogs by age
dog_list.sort(key=lambda dog: dog.age)

for dog in dog_list:
  print(dog.name)
>>> Ema
>>> Leon
>>> Gina
```
