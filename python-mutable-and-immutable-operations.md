
# 🐍 Python Mutable and Immutable Operations

### Mutating Methods

- Mutating methods modify the original object.
- The changes are made directly to the existing collection.

### Non-Mutating Methods

- Non-mutating methods do not modify the original object.
- They return a result or a new object.
- The original collection remains unchanged.

**Important:** Lists and dictionaries are mutable, whereas strings are immutable.

---

# List Operations

## Mutating List Methods

These methods modify the original list.

### 1. `append()`

Adds one element at the end of the list.

```python
numbers = [10, 20, 30]

numbers.append(40)

print(numbers)  # [10, 20, 30, 40]
```

### 2. `extend()`

Adds multiple elements from an iterable to the end of the list.

```python
numbers = [10, 20]

numbers.extend([30, 40])

print(numbers)  # [10, 20, 30, 40]
```

### 3. `insert()`

Inserts an element at a specific index.

```python
numbers = [10, 20, 40]

numbers.insert(2, 30)

print(numbers)  # [10, 20, 30, 40]
```

### 4. `remove()`

Removes the first occurrence of a given value.

```python
numbers = [10, 20, 30, 20]

numbers.remove(20)

print(numbers)  # [10, 30, 20]
```

### 5. `pop()`

Removes and returns an element from the list.

```python
numbers = [10, 20, 30]

removed_element = numbers.pop()

print(removed_element)  # 30
print(numbers)          # [10, 20]
```

We can also provide an index:

```python
numbers = [10, 20, 30]

removed_element = numbers.pop(1)

print(removed_element)  # 20
print(numbers)          # [10, 30]
```

### 6. `clear()`

Removes all elements from the list.

```python
numbers = [10, 20, 30]

numbers.clear()

print(numbers)  # []
```

### 7. `sort()`

Sorts the original list.

```python
numbers = [40, 10, 30, 20]

numbers.sort()

print(numbers)  # [10, 20, 30, 40]
```

Descending order:

```python
numbers = [40, 10, 30, 20]

numbers.sort(reverse=True)

print(numbers)  # [40, 30, 20, 10]
```

### 8. `reverse()`

Reverses the order of elements in the original list.

```python
numbers = [10, 20, 30, 40]

numbers.reverse()

print(numbers)  # [40, 30, 20, 10]
```

---

##  Non-Mutating List Methods and Operations

These methods and operations do not modify the original list.

### 1. `count()`

Returns the number of occurrences of a value.

```python
numbers = [10, 20, 10, 30, 10]

result = numbers.count(10)

print(result)   # 3
print(numbers)  # [10, 20, 10, 30, 10]
```

### 2. `index()`

Returns the index of the first occurrence of a value.

```python
numbers = [10, 20, 30, 20]

result = numbers.index(20)

print(result)   # 1
print(numbers)  # [10, 20, 30, 20]
```

### 3. `copy()`

Returns a shallow copy of the list.

```python
numbers = [10, 20, 30]

new_numbers = numbers.copy()

new_numbers.append(40)

print(numbers)      # [10, 20, 30]
print(new_numbers)  # [10, 20, 30, 40]
```

### 4. `deepcopy()`

Returns a deep copy of the list.

```python
numbers = [10, 20, 30]

new_numbers = numbers.deepcopy()

new_numbers.append(40)

print(numbers)      # [10, 20, 30]
print(new_numbers)  # [10, 20, 30, 40]
```

### 5. `sorted()`

Returns a new sorted list without modifying the original list.

```python
numbers = [40, 10, 30, 20]

new_numbers = sorted(numbers)

print(new_numbers)  # [10, 20, 30, 40]
print(numbers)      # [40, 10, 30, 20]
```

Descending order:

```python
numbers = [40, 10, 30, 20]

new_numbers = sorted(numbers, reverse=True)

print(new_numbers)  # [40, 30, 20, 10]
```

### 6. `reversed()`

Returns an iterator that provides elements in reverse order. It does not modify the original list.

```python
numbers = [10, 20, 30, 40]

new_numbers = list(reversed(numbers))

print(new_numbers)  # [40, 30, 20, 10]
print(numbers)      # [10, 20, 30, 40]
```

---

## Difference Between `copy()` and `deepcopy()`

Before understanding these methods, let's understand shallow copy and deep copy.

## Shallow Copy

- Creates a new outer collection.
- Nested mutable objects are not copied; they are shared with the original collection.
- Changes to first-level elements do not affect the original collection.
- Changes to nested mutable objects affect both collections.

```python
import copy

original = [5, [10, 20], [30, 40]]

shallow_copy = copy.copy(original)

# Update first-level element
shallow_copy[0] = 6

# Update nested-level element
shallow_copy[1][0] = 7

print("Copied:", shallow_copy)
# [6, [7, 20], [30, 40]]

print("Original:", original)
# [5, [7, 20], [30, 40]]
```

Here, both lists refer to the same nested list objects.

## Deep Copy

- Creates a new outer collection and recursively copies nested objects.
- Nested mutable objects are not shared with the original collection.
- Changes to nested objects in the copied collection do not affect the original.

```python
import copy

original = [[10, 20], [30, 40]]

deep_copy = copy.deepcopy(original)

# Modify a nested list
deep_copy[0].append(50)

print(original)
# [[10, 20], [30, 40]]

print(deep_copy)
# [[10, 20, 50], [30, 40]]
```

## Custom `deep_copy()` Function

We can implement our own deep copy function using recursion.

```python
def deep_copy(lst):

    res = []

    for element in lst:

        if type(element) is list:
            inner_list = deep_copy(element)
            res.append(inner_list)

        else:
            res.append(element)

    return res
```
---

# Dictionary Operations

##  Mutating Dictionary Methods

These methods modify the original dictionary.

### 1. Adding and Updating Values

We can add a new key or update an existing key using assignment.

```python
artist = {
    "name": "Skrillex",
    "age": 37  
}

# Update an existing key
artist["age"] = 38

# Add a new key
artist["city"] = "Los Angeles"

print(artist)
# {'name': 'Skrillex', 'age': 38, 'city': 'Los Angeles'}
```

## Mutating Dictionary Methods

These methods modify the original dictionary.

### 1. `update()`

Adds multiple key-value pairs or updates existing ones.

```python
student = {
    "name": "Arvind",
    "age": 20
}

student.update({
    "age": 21,
    "course": "Python"
})

print(student)
# {'name': 'Arvind', 'age': 21, 'course': 'Python'}
```

### 2. `setdefault()`

Adds a key with a default value if the key does not exist.

If the key already exists, its existing value is returned without modification.

```python
student = {
    "name": "Arvind"
}

student.setdefault("age", 20)

print(student)
# {'name': 'Arvind', 'age': 20}
```

### 3. `pop()`

Removes a specified key and returns its value.

```python
student = {
    "name": "Arvind",
    "age": 20
}

removed_value = student.pop("age")

print(removed_value)  # 20
print(student)        # {'name': 'Arvind'}
```

### 4. `popitem()`

Removes and returns the last inserted key-value pair.

```python
student = {
    "name": "Arvind",
    "age": 20,
    "course": "Python"
}

removed_item = student.popitem()

print(removed_item)  # ('course', 'Python')
print(student)       # {'name': 'Arvind', 'age': 20}
```

### 5. `clear()`

Removes all key-value pairs.

```python
student = {
    "name": "Arvind",
    "age": 20
}

student.clear()

print(student)  # {}
```

---

## Non-Mutating Dictionary Methods

These methods do not modify the original dictionary.

### 1. `get()`

Returns the value of a key. If the key does not exist, it returns `None` by default.

```python
student = {
    "name": "Arvind",
    "age": 20
}

print(student.get("name"))       # Arvind
print(student.get("course"))     # None
print(student.get("course", 0))  # 0

print(student)
```

### 2. `keys()`

Returns a view containing all dictionary keys.

```python
student = {
    "name": "Arvind",
    "age": 20
}

result = student.keys()

print(result)
# dict_keys(['name', 'age'])
```

### 3. `values()`

Returns a view containing all dictionary values.

```python
student = {
    "name": "Arvind",
    "age": 20
}

result = student.values()

print(result)
# dict_values(['Arvind', 20])
```

### 4. `items()`

Returns a view containing key-value pairs as tuples.

```python
student = {
    "name": "Arvind",
    "age": 20
}

result = student.items()

print(result)
# dict_items([('name', 'Arvind'), ('age', 20)])
```

### 5. `copy()`

Returns a shallow copy of the dictionary.

```python
student = {
    "name": "Arvind",
    "age": 20
}

new_student = student.copy()

new_student["age"] = 21

print(student)      # {'name': 'Arvind', 'age': 20}
print(new_student)  # {'name': 'Arvind', 'age': 21}
```


# String Operations

A string is an immutable sequence of characters.

- Strings are immutable, meaning we cannot modify their existing characters.
- String methods return new strings instead of modifying the original string.

##  Trying to Modify a String

```python
text = "Python"

# Trying to modify the first character
text[0] = "J"

print(text)
```

**Output:**

```text
TypeError: 'str' object does not support item assignment
```

We cannot modify a character directly because strings are immutable.

## String Methods Return New Strings

### Example 1: `upper()`

```python
text = "python"

new_text = text.upper()

print(text)      # python
print(new_text)  # PYTHON
```

### Example 2: `lower()`

```python
text = "HELLO WORLD"

new_text = text.lower()

print(text)      # HELLO WORLD
print(new_text)  # hello world
```

### Example 3: `replace()`

```python
text = "Python is easy"

new_text = text.replace("easy", "powerful")

print(text)      # Python is easy
print(new_text)  # Python is powerful
```

