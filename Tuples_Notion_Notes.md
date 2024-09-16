# Tuples

It’s unchanged! 

But faster(than list) and safer.

Valid keys in a dictionary.

```python
x = (1, 2, 3)
print(type(x)) # <class 'tuple'>

x = (1, 2, 3)
x[0] = 4 # TypeError: 'tuple' object does not support item assignment
x.append(4) # AttributeError: 'tuple' object has no attribute 'append'

# creating and accessing
first_tuple = (1, 2, 3, 4, 6)
print(first_tuple[0]) # 1
print(first_tuple[-1]) # 6

# Tuple can be used as keys in a dictionary
locations = {
    (35.6895, 39.6917): "Tokyo Office",
    (48.8566, 2.3522): "Paris Office",
    (52.5200, 13.4050): "Berlin Office",
    (55.7558, 37.6173): "Moscow Office",
}
print(locations[(35.6895, 39.6917)]) # Tokyo Office

locs = {[35, 37]: "place"} # TypeError: unhashable type: 'list'

print(locations.items())
# dict_items([((35.6895, 39.6917), 'Tokyo Office'), ((48.8566, 2.3522), 'Paris Office'), ((52.52, 13.405), 'Berlin Office'), ((55.7558, 37.6173), 'Moscow Office')])

names = ("Jessi", "Hellen", "Bob", "Ted")
for name in names:
    print(name)
# Jessi
# Hellen
# Bob
# Ted

numbers = (1, 2, 2, 3, 4, 5, 5, 5, 7)
print(numbers.count(2)) # 2
print(numbers.count(5)) # 3

numbers = (1, 2, 2, 3, 4, 5, 5, 5, 7)
print(numbers.index(3)) # 3(the index of number 3)
print(numbers.index(7)) # 8(the index of number 7)
print(numbers.index(9)) # ValueError: tuple.index(x): x not in tuple

numbers = (1, 2, 2, (3, 4, 5), 5, 5, 7)
print(numbers[3]) # (3, 4, 5)
print(numbers[3][2]) # 5
print(numbers[1:]) # (2, 2, (3, 4, 5), 5, 5, 7)
print(numbers[:4]) # (1, 2, 2, (3, 4, 5))
print(numbers[::2]) # (1, 2, 5, 7)

# Create a variable called value which is a tuple with the the value 1 inside.
value = (1,)
```

## Set comprehension

```python
var = {x ** 2 for x in range(1, 10)}
print(var) # {64, 1, 4, 36, 9, 16, 49, 81, 25}

var = {x: x ** 2 for x in range(1, 10)}
print(var) # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}

var = {char.upper() for char in "hello"}
print(var) # {'h': 'H', 'e': 'E', 'l': 'L', 'o': 'O'}

string = "sequoia"
var = len({char for char in string if char in "aeiou"}) == 5
print(var) # True

string = "hello"
var = len({char for char in string if char in "aeiou"}) == 5
print(var) # False
```