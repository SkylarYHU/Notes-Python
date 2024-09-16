# Sets

1. Like formal mathematical sets
2. Do not have duplicate values
3. Aren’t ordered
4. Can’t not accessed by index

## Intro to sets

```python
s = {1, 4, 5}
print(s) # {1, 4, 5}
print(1 in s) # True
print(3 in s) # False

s = {1, 4, 4, 5, 7, 8, 8}
print(s) # {1, 4, 5, 7, 8}

# the order would chanage
s = {2, "a", 4, "cat", 7.98, 8, 8}
print(s) # {2, 4, 'a', 7.98, 'cat', 8}

for item in s:
    print(item)
# 2
# 4
# a
# cat
# 7.98
# 8

# a common use case: to remove the duplicate values
cities = [
    "Tokyo",
    "New York",
    "Beijing",
    "London",
    "Berlin",
    "Tokyo",
    "Beijing",
    "Toronto"
]

print(set(cities))
# {'New York', 'Berlin', 'Toronto', 'London', 'Tokyo', 'Beijing'}
print(list(set(cities)))
# ['London', 'Berlin', 'Tokyo', 'Beijing', 'New York', 'Toronto']
print(len(set(cities))) # 6 (the real number of cities)

```

## Set methods and set math

```python
# .add()
s = set([1, 3, 4, 8])
s.add(10) 
print(s) # {1, 3, 4, 8, 10}
s.add(10)
print(s) # {1, 3, 4, 8, 10}

# .remove()
s = set([1, 3, 4, 8])
s.remove(3)
print(s) # {8, 1, 4}

s.remove(2)
print(s) # KeyError: 2

# .discard()
s = set([1, 3, 4, 8])
s.discard(3)
print(s) # {8, 1, 4}

s.discard(2)
print(s) # {8, 1, 3, 4} (Nothing happened)

# .copy()
s = set([1, 3, 4, 8])
new_s = s.copy()
print(new_s) # {8, 1, 3, 4}
print(s is new_s) # False
print(s == new_s) # True

# .clear()
s = set([1, 3, 4, 8])
s.clear()
print(s) # set()

# union
math_student = {"Alice", "Bob", "Charlie", "David", "Eva"}
biology_student = {"Alice", "Bob", "Ivy", "Jack", "Katherine"}
print(math_student | biology_student) # {'Katherine', 'Bob', 'Alice', 'Eva', 'Ivy', 'Jack', 'David', 'Charlie'}
print(math_student & biology_student) # {'Alice', 'Bob'}

```