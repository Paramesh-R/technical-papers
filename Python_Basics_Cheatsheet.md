# Python Basics:

### Variables and data types

```
# Variables
name = "John"
age = 25
salary = 45000.50
is_active = True

# Data types
type(name)       # str
type(age)        # int
type(salary)     # float
type(is_active)  # bool

# Type conversion
int("10")
float("10.5")
str(100)
list((1, 2, 3))

```

---

### Input and output

```
# Output
print("Hello World")
print("Name:", name)

# Formatted string
print(f"My name is {name} and I am {age}")

# Input
name = input("Enter your name: ")
age = int(input("Enter your age: "))
```

---

### Operators

```
Operator	Meaning	Example
+	Addition	10 + 5
-	Subtraction	10 - 5
*	Multiplication	10 * 5
/	Division	10 / 5
//	Floor division	10 // 3
%	Modulus	10 % 3
**	Exponent	2 ** 3
==	Equal	a == b
!=	Not equal	a != b
and	Logical AND	a and b
or	Logical OR	a or b
not	Logical NOT	not a
```

---

### Loops

```
# For loop
for i in range(5):
    print(i)

# While loop
i = 0
while i < 5:
    print(i)
    i += 1

# Loop control
break       # Exit loop
continue    # Skip current iteration
pass        # Do nothing
```

---

### Strings

```
text = "Python Programming"

# Access characters
text[0]
text[-1]

# Slicing
text[0:6]
text[:6]
text[7:]

# Common methods
text.lower()
text.upper()
text.title()
text.capitalize()
text.strip()
text.replace("Python", "Java")
text.split()
text.startswith("Python")
text.endswith("Programming")
text.find("Pro")
text.count("m")

# String joining
" ".join(["Hello", "World"])
```

---

### Lists

```
numbers = [10, 20, 30, 40]

# Access
numbers[0]
numbers[-1]

# Modify
numbers[0] = 100

# Add
numbers.append(50)
numbers.extend([60, 70])
numbers.insert(1, 15)

# Remove
numbers.remove(20)
numbers.pop()
numbers.pop(0)
numbers.clear()

# Other operations
len(numbers)
sum(numbers)
min(numbers)
max(numbers)
sorted(numbers)
numbers.reverse()
numbers.count(10)
numbers.index(30)
```

---

### Tuples

```
numbers = (10, 20, 30)

numbers[0]
len(numbers)
numbers.count(10)
numbers.index(20)

# Tuple unpacking
a, b, c = numbers
```

Note: Tuples are immutable. You cannot directly modify their elements.

---

### Sets:

```
numbers = {10, 20, 30}

numbers.add(40)
numbers.update([50, 60])
numbers.remove(20)
numbers.discard(100)

# Set operations
a = {1, 2, 3}
b = {3, 4, 5}

a.union(b)
a.intersection(b)
a.difference(b)
a.symmetric_difference(b)
```

Notes: Sets store unique elements and do not support indexing.

---

### Dictionaries

```
student = {
    "name": "John",
    "age": 25,
    "grade": "A"
}

# Access
student["name"]
student.get("age")

# Add or update
student["city"] = "Chennai"
student["age"] = 26

# Remove
student.pop("grade")
student.popitem()

# Dictionary methods
student.keys()
student.values()
student.items()

# Loop
for key, value in student.items():
    print(key, value)
```

---

### Functions

```
# Basic function
def greet():
    print("Hello")

# Parameters
def add(a, b):
    return a + b

# Default argument
def greet(name="John"):
    print(f"Hello {name}")

# Arbitrary positional arguments
def total(*args):
    return sum(args)

# Arbitrary keyword arguments
def details(**kwargs):
    print(kwargs)
```

---

### Lambda, map, filter and reduce

```
# Lambda
square = lambda x: x ** 2

# Map: Transform elements
numbers = [1, 2, 3]
list(map(lambda x: x * 2, numbers))

# Filter: Select elements
list(filter(lambda x: x % 2 == 0, numbers))

# Reduce: Combine elements
from functools import reduce

reduce(lambda a, b: a + b, numbers)

# Sorted with key
students = [("John", 25), ("Sam", 20)]
sorted(students, key=lambda x: x[1])
```

---

### Exception handling

```
try:
    result = 10 / 0

except ZeroDivisionError:
    print("Cannot divide by zero")

except Exception as e:
    print(e)

else:
    print("No errors")

finally:
    print("Always executes")
```

---

### File handling

```
# Read
with open("data.txt", "r") as file:
    content = file.read()

# Read line by line
with open("data.txt", "r") as file:
    for line in file:
        print(line)

# Write
with open("data.txt", "w") as file:
    file.write("Hello Python")

# Append
with open("data.txt", "a") as file:
    file.write("\nNew line")
```

---

### List comprehensions

```
numbers = [1, 2, 3, 4, 5]

# Basic
squares = [x ** 2 for x in numbers]

# With condition
even = [x for x in numbers if x % 2 == 0]

# If-else
result = ["Even" if x % 2 == 0 else "Odd"
          for x in numbers]
```

---
