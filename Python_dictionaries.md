# Python Dictionaries – Cheat Sheet

## What is a Dictionary?

A dictionary is a built-in Python data structure used to store data in **key-value pairs**.

Each item contains:

- **Key:** Identifies the data.
- **Value:** Stores the actual data.

### Characteristics

- Ordered (insertion order is preserved).
- Mutable (can be modified).
- Keys must be unique.
- Keys must be hashable.
- Values can be of any data type.

### Example

```python
student = {
    "name": "John",
    "age": 25,
    "department": "Computer Science"
}
```

---

## Creating Dictionaries

### Using curly braces

```python
student = {
    "name": "John",
    "age": 25
}
```

### Using dict()

```python
student = dict(name="John", age=25)
```

### Creating an empty dictionary

```python
student = {}
student = dict()
```

### Using a list of tuples

```python
student = dict([
    ("name", "John"),
    ("age", 25)
])
```

### Using fromkeys()

```python
keys = ["name", "age", "city"]

student = dict.fromkeys(keys, None)
```

Output:

```text
{'name': None, 'age': None, 'city': None}
```

---

## Accessing Dictionary Elements

### Using keys

```python
student = {
    "name": "John",
    "age": 25
}

print(student["name"])
print(student["age"])
```

### Using get()

```python
print(student.get("name"))
```

### Difference between [] and get()

```python
student["city"]       # Raises KeyError
student.get("city")   # Returns None
```

### Providing a default value

```python
print(student.get("city", "Not Available"))
```

---

## Adding Dictionary Elements

### Using assignment

```python
student = {"name": "John", "age": 25}

student["city"] = "Chennai"
```

### Using update()

```python
student.update({
    "department": "IT",
    "salary": 50000
})
```

`update()` adds new keys and updates existing keys.

---

## Updating Dictionary Elements

```python
student = {
    "name": "John",
    "age": 25
}

student["age"] = 26
```

### Using update()

```python
student.update({"age": 27})
```

---

## Removing Dictionary Elements

| Method      | Description                                  |
| ----------- | -------------------------------------------- |
| `pop(key)`  | Removes specified key and returns its value  |
| `popitem()` | Removes and returns the last inserted pair   |
| `del`       | Deletes a specified key or entire dictionary |
| `clear()`   | Removes all dictionary elements              |

### pop()

```python
student.pop("age")
```

### popitem()

```python
student.popitem()
```

### del

```python
del student["name"]
```

### Delete entire dictionary

```python
del student
```

### clear()

```python
student.clear()
```

---

## Dictionary Methods

| Method         | Description                          |
| -------------- | ------------------------------------ |
| `keys()`       | Returns all dictionary keys          |
| `values()`     | Returns all dictionary values        |
| `items()`      | Returns key-value pairs              |
| `get()`        | Returns value for a specified key    |
| `update()`     | Adds or updates elements             |
| `pop()`        | Removes a specified key              |
| `popitem()`    | Removes the last inserted item       |
| `clear()`      | Removes all elements                 |
| `copy()`       | Creates a shallow copy               |
| `setdefault()` | Returns value or inserts a default   |
| `fromkeys()`   | Creates a dictionary from given keys |

### keys()

```python
student = {"name": "John", "age": 25}

print(student.keys())
```

### values()

```python
print(student.values())
```

### items()

```python
print(student.items())
```

### setdefault()

```python
student = {"name": "John"}

student.setdefault("age", 25)

print(student)
```

If the key exists, its value remains unchanged.

### copy()

```python
new_student = student.copy()
```

Creates a shallow copy.

---

## Iterating Through Dictionaries

### Iterate through keys

```python
for key in student:
    print(key)
```

### Iterate through values

```python
for value in student.values():
    print(value)
```

### Iterate through key-value pairs

```python
for key, value in student.items():
    print(key, value)
```

---

## Dictionary Membership Operators

Use `in` and `not in` to check whether a key exists.

```python
student = {
    "name": "John",
    "age": 25
}

print("name" in student)
print("city" not in student)
```

### Check whether a value exists

```python
print("John" in student.values())
```

**Important:** Dictionary membership checks keys by default, not values.

---

## Dictionary Length

Use `len()` to find the number of key-value pairs.

```python
student = {
    "name": "John",
    "age": 25,
    "city": "Chennai"
}

print(len(student))
```

Output: `3`

---

## Dictionary Comprehension

Dictionary comprehension creates dictionaries using a single expression.

### Syntax

```python
{key_expression: value_expression for item in iterable}
```

### Example 1: Squares of numbers

```python
squares = {
    x: x ** 2
    for x in range(1, 6)
}
```

Output:

```text
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

### Example 2: Conditional comprehension

```python
even_numbers = {
    x: x ** 2
    for x in range(1, 11)
    if x % 2 == 0
}
```

### Example 3: Convert a list into a dictionary

```python
names = ["John", "David", "Sam"]

name_lengths = {
    name: len(name)
    for name in names
}
```

---

## Nested Dictionaries

A dictionary can contain another dictionary as its value.

```python
students = {
    "student1": {
        "name": "John",
        "age": 25
    },
    "student2": {
        "name": "David",
        "age": 26
    }
}
```

### Accessing nested values

```python
print(students["student1"]["name"])
```

### Updating nested values

```python
students["student1"]["age"] = 27
```

### Iterating nested dictionaries

```python
for student_id, details in students.items():
    print(student_id)

    for key, value in details.items():
        print(key, value)
```

---

## Dictionary Unpacking and Merging

### Using update()

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4}

dict1.update(dict2)
```

### Using | operator (Python 3.9+)

```python
result = dict1 | dict2
```

### Using dictionary unpacking

```python
result = {**dict1, **dict2}
```

**Important:** When duplicate keys exist, the right-hand dictionary's value takes precedence.

---

## Sorting Dictionaries

### Sort by keys

```python
student = {
    "David": 80,
    "John": 90,
    "Alice": 85
}

result = dict(sorted(student.items()))
```

### Sort by values - ascending

```python
result = dict(
    sorted(student.items(), key=lambda item: item[1])
)
```

### Sort by values - descending

```python
result = dict(
    sorted(
        student.items(),
        key=lambda item: item[1],
        reverse=True
    )
)
```

---

## Dictionary Functions

### Minimum value

```python
min(data.values())
```

### Maximum value

```python
max(data.values())
```

### Sum of values

```python
sum(data.values())
```

### Find key with maximum value

```python
marks = {
    "John": 85,
    "David": 90,
    "Sam": 75
}

topper = max(marks, key=marks.get)

print(topper)
```

Output: `David`

---

## Important Dictionary Concepts

### A. Dictionary Keys Must Be Unique

```python
student = {
    "name": "John",
    "age": 25,
    "name": "David"
}
```

Output:

```text
{'name': 'David', 'age': 25}
```

The latest value overwrites the earlier value.

### B. Dictionary Keys Must Be Hashable

Valid keys:

```python
data = {
    "name": "John",
    10: "Number",
    (1, 2): "Tuple"
}
```

Invalid keys:

```python
data = {
    [1, 2]: "List"  # TypeError
}
```

Lists, dictionaries and sets cannot be dictionary keys because they are unhashable.

### C. Dictionaries Are Mutable

```python
student = {"name": "John"}

student["name"] = "David"
```

### D. Dictionaries Preserve Insertion Order

```python
data = {}

data["a"] = 1
data["b"] = 2
data["c"] = 3
```

Insertion order preservation is guaranteed from Python 3.7 onwards.

---

## Shallow Copy vs Deep Copy

### Shallow Copy

Creates a new dictionary, but nested mutable objects are shared.

```python
import copy

original = {
    "name": "John",
    "marks": [80, 90]
}

new_data = copy.copy(original)

new_data["marks"].append(95)

print(original["marks"])
```

Output:

```text
[80, 90, 95]
```

### Deep Copy

Creates independent copies of nested objects.

```python
new_data = copy.deepcopy(original)

new_data["marks"].append(100)

print(original["marks"])
```

The original nested list remains unchanged by the deep copy operation.

---

## Useful Dictionary Patterns

### Count frequency of elements

```python
numbers = [1, 2, 2, 3, 3, 3, 4]

frequency = {}

for num in numbers:
    frequency[num] = frequency.get(num, 0) + 1

print(frequency)
```

Output:

```text
{1: 1, 2: 2, 3: 3, 4: 1}
```

### Group elements by category

```python
students = [
    ("John", "A"),
    ("David", "B"),
    ("Sam", "A"),
    ("Alex", "B")
]

groups = {}

for name, grade in students:
    groups.setdefault(grade, []).append(name)
```

Output:

```text
{'A': ['John', 'Sam'], 'B': ['David', 'Alex']}
```

### Find common keys

```python
dict1 = {"a": 1, "b": 2, "c": 3}
dict2 = {"b": 20, "c": 30, "d": 40}

common_keys = dict1.keys() & dict2.keys()
```

### Find keys with maximum values

```python
marks = {
    "John": 85,
    "David": 90,
    "Sam": 90
}

highest = max(marks.values())

top_students = [
    name
    for name, score in marks.items()
    if score == highest
]
```

---

## defaultdict - Collections Module

`defaultdict` is a dictionary subclass from the `collections` module.

It automatically creates a default value when accessing a missing key.

```python
from collections import defaultdict

frequency = defaultdict(int)

numbers = [1, 2, 2, 3, 3, 3]

for num in numbers:
    frequency[num] += 1

print(dict(frequency))
```

Output:

```text
{1: 1, 2: 2, 3: 3}
```

### Common default factories

| Factory | Default value |
| ------- | ------------- |
| `int`   | `0`           |
| `list`  | `[]`          |
| `set`   | `set()`       |
| `str`   | `""`          |

### Example using defaultdict(list)

```python
from collections import defaultdict

groups = defaultdict(list)

groups["A"].append("John")
groups["A"].append("Sam")
groups["B"].append("David")

print(dict(groups))
```

---

## Counter - Collections Module

`Counter` is a dictionary subclass used to count the frequency of elements.

```python
from collections import Counter

numbers = [1, 2, 2, 3, 3, 3, 4]

frequency = Counter(numbers)

print(frequency)
```

Output:

```text
Counter({3: 3, 2: 2, 1: 1, 4: 1})
```

### Find most common elements

```python
frequency.most_common(2)
```

Output:

```text
[(3, 3), (2, 2)]
```

---

## Dictionary vs List vs Set vs Tuple

| Feature    | Dictionary          | List     | Set                 | Tuple    |
| ---------- | ------------------- | -------- | ------------------- | -------- |
| Syntax     | `{key: value}`      | `[]`     | `{}`                | `()`     |
| Ordered    | Yes                 | Yes      | No guaranteed order | Yes      |
| Mutable    | Yes                 | Yes      | Yes                 | No       |
| Duplicates | Keys: No            | Yes      | No                  | Yes      |
| Access     | By key              | By index | No indexing         | By index |
| Lookup     | O(1) average by key | O(n)     | O(1) average        | O(n)     |

---
