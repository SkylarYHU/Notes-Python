# Functions

## Why use functions?

1. Stay DRY - Don’t repeat yourself!
2. Abstract away code for other users

## Defining functions

```python
def say_hi():
    print("Hi")

 
say_hi() # Hi
```

## The Magical Return Keyword

```python
def square_of_7():
    return 7 ** 2

result = square_of_7()
print(result) # 49
```

```python
def square_of_7():
    print("I am after the return!") # can input normally
    return 7 ** 2
    print("I am after the return!") # The code is unreachable 

result = square_of_7()
print(result)

```

## return

1. Exit the function
2. Outputs whatever value is placed after the return keyword
3. Pops the function off of the call stack

```python
from random import random

def flip_coin():
    r = random()
    if r > 0.5:
        return "Heads"
    else:
        return "Tails"

print(flip_coin())

# --------------------------------------------
# overwrite
from random import random

def flip_coin(): # The version is lost
    r = random()
    if r > 0.5:
        return "Heads"
    else:
        return "Tails"

def flip_coin(): # Just active this function
    r = random()
    if r > 0.5:
        return "H"
    else:
        return "T"

print(flip_coin())

# --------------------------------------------
def generate_evens():
    return [x for x in range(1,50) if x%2 == 0]

```

## Parameters

```python
def square(num):
    return num ** 2

print(square(2)) # 4
print(square(5)) # 25

# --------------------------------------------
def add(a, b):
    return a + b

print(add(3, 6)) # 9

# --------------------------------------------
def full_name(first_name, last_name):
    return f"You full name is {first_name} {last_name}"

print(full_name("Skylar", "Hu"))
```

## Parameters Vs. Arguments

```python
def full_name(first_name, last_name): # parameters
    return f"You full name is {first_name} {last_name}"

print(full_name("Skylar", "Hu")) # arguments
```

## Common Mistakes When Returning

```python
# Unnecessary "else"
def evens(num):
    if num % 2 == 0:
        return True
    else:
        return False
print(evens(6))

#-------------better version-------------
def evens(num):
    if num % 2 == 0:
        return True # if meets the condition, quit the function
    return False # if doesn't meet the condition, perform this statement
print(evens(6))
```

## Default parameters

```python
def exponent(num, power):
    return num ** power
print(exponent(2, 3)) # 8
print(exponent(2)) # TypeError: exponent() missing 1 required positional argument: 'power'

# set the default value for parameters
def exponent(num, power=2):
    return num ** power 
print(exponent(2, 3)) # 8
print(exponent(2)) # 4

def add(a=10, b=20):
    return a + b
print(add()) # 30
print(add(4, 5)) # 9

#-------------------------------------------------------
def show_information(first_name="Colt", is_instructor=False):
    if first_name == "Colt" and is_instructor:
        return "Welcome back instructor Colt!"
    elif first_name == "Colt":
        return "I really thought you were an instructor!"
    return f"Hello {first_name}!"

print(show_information("Colt", True))
print(show_information("Colt"))
print(show_information("Skylar"))

#------------------------------------------------------- 
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def operate(a, b, fn=add):
    return fn(a, b)

print(operate(3, 4)) # 7
print(operate(3, 4, subtract)) # -1
```

## Keyword arguments

A little more flexibility

```python
def full_name(first, last):
    return f"Hello {first} {last}"

print(full_name(first="Skylar", last="Hu")) # Hello Skylar Hu 
print(full_name(last="Yen", first="Fia")) # Hello Fia Yen
```

## Scope

```python
# Global scope
# 不会报错：因为只是访问了全局变量 instructor，并没有在函数内部对它进行修改。
# 因此，Python 可以直接找到全局变量 instructor 并使用它。
instructor = "Colt"
def say_hi():
    return f"Hi {instructor}"
print(say_hi()) # Hi Colt

def say_hi():
    instructor = "Colt"
    return f"Hi {instructor}"

print(say_hi(instructor)) # name 'instructor' is not defined

# 会报错：因为在 increment() 函数中，你试图修改 total 变量的值
# 但 Python 在看到 total += 1 之前会认为 total 是一个局部变量。
total = 0
def increment():
    total += 1 # manipulate导致报错
    return total
increment() # UnboundLocalError: cannot access local variable 'total' where it is not associated with a value

total = 0
def increment():
    global total
    total += 1 
    return total
print(increment()) # 1

total = 0
def increment():
    total = 3 # 重新赋值并不会导致报错
    return total
print(increment())  # 3
```

## Docstrings and Functions Recap

```python
def say_hello():
    """ A simple function that returns the string hello"""
    return "Hello!"

print(say_hello.__doc__)
```

## if i Vs. if i != False

- This checks the **truthiness** of `i`
    
    **Falsy values** include: `0`, `False`, `None`, `""` (empty string), `[]` (empty list), `{}` (empty dictionary), and `()` (empty tuple).
    
- if i != False
    
    This checks if `i` is **not exactly equal to `False`**
    

```python
def compact(l):
    return [i for i in l if i]
print(compact([0,1,2,"",[], False, {}, None, "All done"]))
# [1,2, "All done"]
```

## *args (Tuple)

```python
def sum_all_num(num1, num2, num3, num4): # we have to set many parameters
    return num1 + num2 + num3 + num4
print(sum_all_num(4, 6, 7, 9)) # 26

# Use *arg to set any number of parameters
def sum_all_num(*args):
    total = 0
    for n in args:
        total += n
    return total

print(sum_all_num(4, 6, 7, 9)) # 26
print(sum_all_num(4, 6)) # 10
print(sum_all_num(4, 6, 7)) # 17

# We can also add other parameters before *args
def sum_all_num(num, *args):
    print(num)
    total = 0
    for n in args:
        total += n
    return total

print(sum_all_num(4, 6, 7, 9)) # 22
print(sum_all_num(4, 6)) # 6
print(sum_all_num(4, 6, 7)) # 13

# -----------------------------------------------
def ensure_correct_info(*args):
		print(args) # (1, True, 'Skylar', 'Hu')
    if "Skylar" in args and "Hu" in args:
        return "Welcome back Skylar!"
    return "Not sure who you are..."

print(ensure_correct_info(1, True, "Skylar", "Hu"))
# Welcome back Skylar!
```

## **kwargs

`**kwargs` 将传递的关键字参数（键值对）作为 **字典** 传入函数内部

```python
def fav_colors(**kwargs):
    print(kwargs) 
    # {'Lucy': 'Purple', 'Lisa': 'Green', 'Ted': 'Brown'}

fav_colors(Lucy="Purple", Lisa="Green", Ted="Brown")

def fav_colors(**kwargs):
    for person, color in kwargs.items():
        print(f"{person} loves {color}")
        
fav_colors(Lucy="Purple", Lisa="Green", Ted="Brown")
# Lucy loves Purple
# Lisa loves Green
# Ted loves Brown

def greeting(**kwargs):
    if "David" in kwargs and kwargs["David"] == "special":
        return "You get a special greeting David!"
    elif "David" in kwargs:
        return f"{kwargs["David"]} David!"
    return "Not sure who this is..."

print(greeting(David="Hello"))
print(greeting(Bob="hello"))
print(greeting(David="special"))
```

## Parameter Ordering

1. parameters
2. *args
3. default parameters
4. **kwargs
5. 

```python
def display_info(a, b, *args, instructor="Colt", **kwargs):
    return [a, b, args, instructor, kwargs]
print(display_info(1, 2, 3, last_name="Steele", job="Instructor"))
# [1, 2, (3,), 'Colt', {'last_name': 'Steele', 'job': 'Instructor'}]
```

## Tuple unpacking

```python
def sum_all_values(*args):
    print(args)
    total = 0
    for num in args:
        total += num
    return total

num = [1,2,3,4,5]
print(sum_all_values(num)) # （[1,2,3,4,5]）
# TypeError: unsupported operand type(s) for +=: 'int' and 'list'

def sum_all_values(*args):
    print(args)
    total = 0
    for num in args:
        total += num
    return total

num = (1,2,3,4,5)
print(sum_all_values(num)) # ((1,2,3,4,5))
# TypeError: unsupported operand type(s) for +=: 'int' and 'tuple'

def sum_all_values(*args):
    print(args) # 15
    total = 0
    for num in args:
        total += num
    return total

num = (1, 2, 3, 4, 5)
print(sum_all_values(*num)) # (1, 2, 3, 4, 5)
```

## Dictionary unpacking

```python
def display_names(first, second):
    print(f"{first} says hello to {second}")

display_names(first="Skylar", second="Hu")
# Skylar says hello to Hu

# ------------------------------------------
def display_names(first, second):
    print(f"{first} says hello to {second}")

names = {"first": "Skylar", "second": "Hu"}
display_names(names)
# TypeError: display_names() missing 1 required positional argument: 'second'

def display_names(first, second):
    print(f"{first} says hello to {second}")

names = {"first": "Skylar", "second": "Hu"}
display_names(**names)
# Skylar says hello to Hu

# ------------------------------------------
def add_multiply(a, b, c, **kwargs):
    print(a + b * c)
    print("OTHER STUFF...")
    print(kwargs)

data = dict(a=1, b=2, c=3, d=5)
add_multiply(**data)
# 7
# OTHER STUFF...
# {'d': 5}
```

## Exercises

```python
'''
calculate(make_float=False, operation='add', message='You just added', first=2, second=4) # "You just added 6"
calculate(make_float=True, operation='divide', first=3.5, second=5) # "The result is 0.7"
'''

def calculate(first, second, make_float=True, operation='add', message=''):
    operations = {
        "add": add,
        "subtract": subtract,
        "multiply": multiply,
        "divide": divide,
    }
     
    operation_fn = operations.get(operation)
    result = operation_fn(first, second)
    if make_float:
        return f"The result is {result}"
    return f"{message} {result}"    

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    return a / b
```