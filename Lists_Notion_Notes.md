# Lists

## List Methods

```python
# index
numbers = [1, 2, 4, 4, 4, 5, 7, 8]
index = numbers.index(2) # 1 (the index of first number 2)
print(index)

numbers = [1, 2, 4, 4, 4, 5, 7, 4, 8, 2, 1, 4]
index1 = numbers.index(4, 3) # number 4 from the index 3
print(index1) # 3
index2 = numbers.index(4, 6, 9) # number 4 betwee n index 6 and index 9
print(index2) # 7

index3 = numbers.index(122)
print(index3) # ValueError: 122 is not in list

# count
numbers = [1, 2, 4, 4, 4, 5, 7, 4, 8, 2, 1, 4]
count1 = numbers.count(2)
print(count1) # 2
count2 = numbers.count(4)
print(count2) # 5
count3 = numbers.count(122)
print(count3) # 0 (Vs. index(122))

# reverse
numbers = [1, 2, 3, 4]
numbers.reverse()
print(numbers) # [4, 3, 2, 1]

# sort
numbers = [8, 4, 3, 1]
numbers.sort()
print(numbers) # [1, 3, 4, 8]

# join
words = ["How", "are", "you!"]
print(" ".join(words)) # How are you!

name = ["Jame", "Smith"]
print(".".join(name)) # Jame.Smith
```

## Slices

```python
numbers = [1, 2, 3, 4]
print(numbers[1:]) # [2, 3, 4]
numbers = [1, 2, 3, 4]
print(numbers[2:]) # [3, 4]

numbers = [1, 2, 3, 4]
print(numbers[-1:]) # [4]

numbers = [1, 2, 3, 4]
print(numbers[:2]) # [1, 2] doesn't include the end index 2

numbers = [1, 2, 3, 4]
print(numbers[1:3]) # [2, 3] doesn't include the end index 3

numbers = [1, 2, 3, 4]
print(numbers[:-1]) # [1, 2, 3]

numbers = [1, 2, 3, 4, 5, 6]
print(numbers[1::2]) # [2, 4, 6] 
# start from index 1 till the end and the step is 2

numbers = [1, 2, 3, 4, 5, 6]
print(numbers[::2]) # [1, 3, 5]

# Tricks with slice
words = "Have a great day!"
print(words[::-1]) # !yad taerg a evaH

numbers = [1, 2, 3, 4, 5, 6]
numbers[1:4] = ["a", "b", "c"]
print(numbers) [1, 'a', 'b', 'c', 5, 6]

```

## Swapping Values in List

```python
names = ["Hu", "Skylar"]
names[0], names[1] = names[1], names[0]
print(names) # ['Skylar', 'Hu']
```

## List Comprehension

```python
numbers = [1,2,3,4]
var = [number * 10 for number in numbers]
print(var) # [10, 20, 30, 40]

# list comprehension Vs. Loop
numbers = [1,2,3,4]
double_numbers = []
for num in numbers:
    double_num = num * 2
    double_numbers.append(double_num)
print(double_numbers) # [2, 4, 6, 8]

numbers = [1, 2, 3, 4]
double_numbers = [num * 2 for num in numbers]
print(double_numbers) # [2, 4, 6, 8]

# more examples
names = ["c", "o", "l", "t"]
upper_name = [name.upper() for name in names]
print(upper_name) # ['C', 'O', 'L', 'T']

friends = ["skylar", "fia", "bob"]
new_friends = [friend.capitalize() for friend in friends]
print(new_friends) # ['Skylar', 'Fia', 'Bob']

# range
new_list = [num * 10 for num in range(1, 5)]
print(new_list)

print([bool(val) for val in [0, "", []]]) # [False, False, False]

numbers = [1, 2, 3, 4, 5]
str_numbers = [str(num) for num in numbers]
print(str_numbers) #['1', '2', '3', '4', '5']
```

## List comprehension with Conditional Logic

```python
numbers = [1, 2, 3, 4, 5, 6]
evens = [num for num in numbers if num % 2 == 0]
odds = [num for num in numbers if num % 2 != 0]
print(evens) # [2, 4, 6]
print(odds) # [1, 3, 5]
print("Evens:" + " ".join(str(num) for num in evens)) # Evens:2 4 6

numbers = [1, 2, 3, 4, 5, 6]
new_numbers = [num * 2 if num % 2 == 0 else num / 2 for num in numbers]
print(new_numbers) # [0.5, 4, 1.5, 8, 2.5, 12]

# check the common items in lists
list1 = [1,2,3,4]
list2 = [3,4,5,6]
answer = [num for num in list1 if num in list2] # [3,4]

# reverse the single string
words = ["Elie", "Tim", "Matt"]
answer2 = [word[::-1].lower() for word in words] # ['eile', 'mit', 'ttam']

vowels = ['a', 'e','i', 'o', 'u']
answer = [char for char in "amazing" if char not in vowels]
print(answer) # ['m', 'z', 'n', 'g']
```

## Nested List

```python
# Access
numbers = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
num1 = numbers[0][1] # 2
num2 = numbers[2][0] # 7
print(num1, num2)

numbers = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
for i in numbers:
    for num in i:
        print(num)
# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9

numbers = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
new_numbers = [[print(n) for n in num] for num in numbers]

# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9

board = [[n for n in range(1, 4)] for num in range(1, 4)]
print(board)
# [[1, 2, 3], [1, 2, 3], [1, 2, 3]]

var = [["X" if n % 2 != 0 else "O" for n in range(1, 4)] for num in range(1,4)]
print(var)
# [['X', 'O', 'X'], ['X', 'O', 'X'], ['X', 'O', 'X']]
```