# Namedtuple

- from `collections` module
- it allows you to create tuple subclasses with named fields
  - it was created to improve code readability by providing a way to access values using descriptive field names instead of integer indices 
- they are also immutable


```python
# Now let's prove they improve readability

# regular tuple
person = ("tamara", 27, "warsaw")
welcome_message = f"This is {person[0]}, she has {person[1]} years and lives in {person[2]}"

# now let's used namedtuple
from collections import namedtuple

Person = namedtuple("Person", ["name", "age", "city"])
p = Person(name="tamara", age=27, city="warsaw")
welcome_message = f"This is {p.name}, she has {p.age} years and lives in {p.city}"
```
