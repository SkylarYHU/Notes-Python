# Dictionaries

## Limitations of Lists

No enough information

## Creating dictionaries

```python
cat = {
    "name": 'Lucy',
    "age": 2,
    "isCute": True
}

print(cat)
```

## Accessing data

```python
# single
cat = {
    "name": 'Lucy',
    "age": 2,
    "isCute": True
}
print(cat["name"]) # Lucy
print(cat["thing"]) # KeyError: 'thing'

# all
cat = {
    "name": 'Lucy',
    "age": 2,
    "isCute": True
}
for value in cat.values():
    print(value)
# Lucy
# 2
# True

for key in cat.keys():
    print(key)
# name
# age
# isCute

for item in cat.items():
    print(item)
# ('name', 'Lucy')
# ('age', 2)
# ('isCute', True)

for key,value in cat.items():
    print(key, value)
# name Lucy
# age 2
# isCute True
```

## Does a dictionary have a key?

```python
# check if a key in the dict
cat = {
    "name": 'Lucy',
    "age": 2,
    "isCute": True
}
print("name" in cat) # True

# check if a value in the dict( doesn't work)
cat = {
    "name": 'Lucy',
    "age": 2,
    "isCute": True
}

print("Lucy" in cat) # False

cat = {
    "name": 'Lucy',
    "age": 2,
    "isCute": True
}
if cat["name"]:
    print("The cat has a name.")
    
# check if a value in the dict(works)
cat = {
    "name": 'Lucy',
    "age": 2,
    "isCute": True
}

print("Lucy" in cat.values()) # True

# check if a key in the dict 
print("name" in cat.keys()) # True

```

## Dictionary Methods

```python
# .clear()
info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems"
}
info.clear()
print(info) # {}

# .copy()
info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems"
}
new_info = info.copy()
print(new_info) # {'name': 'Jasper', 'age': 12, 'major': 'Information Systems'}
print(info == new_info) # True
print(info is new_info) # False

# .fromkeys() to create default dictionaries
new_user = {}.fromkeys(["name", "age", "major"], "unknown")
print(new_user) # {'name': 'unknown', 'age': 'unknown', 'major': 'unknown'}

# pay attention to the first value
new_user = {}.fromkeys("phone", "unknown")
print(new_user) # {'p': 'unknown', 'h': 'unknown', 'o': 'unknown', 'n': 'unknown', 'e': 'unknown'}

new_user = {}.fromkeys(range(1, 5), "unknown")
print(new_user) # {1: 'unknown', 2: 'unknown', 3: 'unknown', 4: 'unknown'}

# .get()
info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems"
}
print(info["name"]) # Jasper
print(info.get("name")) # Jasper

print(info["sex"]) # KeyError: 'sex' 
print(info.get("sex")) # None

# -------------- Example --------------
# This code picks a random food item:
from random import choice #DON'T CHANGE!
food = choice(["cheese pizza", "quiche","morning bun","gummy bear","tea cake"]) #DON'T CHANGE!

#DON'T CHANGE THIS DICTIONARY EITHER!
bakery_stock = {
    "almond croissant" : 12,
    "toffee cookie": 3,
    "morning bun": 1,
    "chocolate chunk cookie": 9,
    "tea cake": 25
}

# YOUR CODE GOES BELOW:
# Solution using IN
if food in bakery_stock:
    print(f"{bakery_stock[food]} left")
else:
    print("We don't make that")

# Solution using get()
quantity = bakery_stock.get(food)
if quantity:
    print(f"{quantity} left")
else:
    print("we don't make that")
    
# .pop()
info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems"
}
info.pop() # TypeError: pop expected at least 1 argument, got 0

info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems"
}
info.pop("name")
print(info) # {'age': 12, 'major': 'Information Systems'}

info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems"
}
info.pop("time") # KeyError: 'time'

# .popitem()
info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems",
    "sex": "male",
    "country": "Ireland"
}
info.popitem() # {'name': 'Jasper', 'age': 12, 'major': 'Information Systems', 'sex': 'male'}
print(info)

info.popitem("age") # TypeError: dict.popitem() takes no arguments (1 given)
print(info)

# .update()
info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems",
}
new_info = {}
new_info.update(info) # {'name': 'Jasper', 'age': 12, 'major': 'Information Systems'}
print(new_info)

info = {
    "name": "Jasper",
    "age": 12,
    "major": "Information Systems",
}
new_info = {"sex": "male"}
new_info.update(info)
print(new_info) # {'sex': 'male', 'name': 'Jasper', 'age': 12, 'major': 'Information Systems'}
```

## Data Modeling

```python
playlist = {
    "title": "patagonia bus",
    "author": "Colt Steele",
    "songs": [{
        "name": "Turn it off",
        "artist": "Culture Abuse",
        "album": "Peach",
        "duration": 3.37
    },
        {
            "name": "Nights off",
            "artist": "Siriusmo",
            "album": "Mosaik",
            "duration": 4.08
        },
        {
            "name": "Don't stop",
            "artist": "Knightlife",
            "album": "Oceans Apart",
            "duration": 6.13
        }
    ]
}
total_length = 0
for time in playlist["songs"]:
    total_length += time["duration"]
print(total_length) #13.58

for song in playlist["songs"]:
    print(song["name"])
# Turn it off
# Nights off
# Don't stop
```

## Dictionary Comprehension

```python
numbers = {
    "a": 1,
    "b": 2,
    "c": 3
}
squared_numbers = {key: value ** 2 for key, value in numbers.items()}
print(squared_numbers) # {'a': 1, 'b': 4, 'c': 9}

var = {num: num ** 2 for num in range(1, 5)}
print(var) # {1: 1, 2: 4, 3: 9, 4: 16}

list1 = ["CA", "NJ", "RI"]
list2 = ["California", "New Jersey", "Rhode Island"]
answer = {list1[i]: list2[i] for i in range(0, len(list1))}
print(answer) # {'CA': 'California', 'NJ': 'New Jersey', 'RI': 'Rhode Island'}

str1 = "ABC"
str2 = "123"
mix = {str1[i]: str2[i] for i in range(0, len(str1))}
print(mix) # {'A': '1', 'B': '2', 'C': '3'}

key_list = ["name", "age", "city"]
val_list = ["Skylar", 23, "Beijing"]
info = {key_list[i]: val_list[i] for i in range(0, len(key_list))}
print(info) # {'name': 'Skylar', 'age': 23, 'city': 'Beijing'}

num_list = [1, 2, 3, 4, 5, 6]
info = {num: ("even" if num % 2 == 0 else "odd") for num in num_list}
print(info) # {1: 'odd', 2: 'even', 3: 'odd', 4: 'even', 5: 'odd', 6: 'even'}

person = [["name", "Jared"], ["job", "Musician"], ["city", "Bern"]]
answer = {thing[0]: thing[1] for thing in person}
print(answer) # {'name': 'Jared', 'job': 'Musician', 'city': 'Bern'}

person = [["name", "Jared"], ["job", "Musician"], ["city", "Bern"]]
answer = dict(person)
print(answer) # {'name': 'Jared', 'job': 'Musician', 'city': 'Bern'}
```