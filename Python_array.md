# Python Array Cheatsheet

### Creating arrays (lists)

```
arr = [10, 20, 30, 40, 50]

# Empty list
arr = []

# Fixed values
arr = [0] * 5

# Range
arr = list(range(5))

# Range with start and end
arr = list(range(1, 6))

# Nested list (2D array)
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

---

### Accessing elements

```
arr = [10, 20, 30, 40, 50]

arr[0]       # First element
arr[-1]      # Last element
arr[-2]      # Second last element
arr[1:4]     # Elements from index 1 to 3
arr[:3]      # First three elements
arr[2:]      # From index 2
arr[::-1]    # Reversed copy
```

---

### Adding Elements:

```
arr.append(60)          # Add at end

arr.insert(1, 15)       # Add at index 1

arr.extend([70, 80])    # Add multiple elements

arr += [90, 100]        # Concatenate lists
```

---

### Removing Elements:

```
arr.remove(20)    # Remove first matching value

arr.pop()         # Remove last element

arr.pop(0)        # Remove element at index 0

del arr[1]        # Delete by index

del arr[1:3]      # Delete a range

arr.clear()       # Remove all elements
```

---

### Searching Elements

```
arr = [10, 20, 30, 40, 50]

30 in arr              # True

arr.index(30)          # Returns index

arr.count(20)          # Count occurrences

40 not in arr          # False
```

---

### Sorting, Reversing:

```
arr = [40, 10, 50, 20, 30]

arr.sort()                  # Ascending

arr.sort(reverse=True)      # Descending

sorted(arr)                 # Returns new sorted list

arr.reverse()               # Reverse in place

arr[::-1]                   # Reversed copy
```

Difference:

- sort() modifies the original list.

- sorted() returns a new sorted list.

- reverse() reverses the original list.

- [::-1] creates a reversed copy.

---

### Iterating through arrays

```
arr = [10, 20, 30, 40]

# Normal iteration
for num in arr:
    print(num)

# Using index
for i in range(len(arr)):
    print(arr[i])

# Using enumerate
for index, value in enumerate(arr):
    print(index, value)

# Iterate with index and value
for i, value in enumerate(arr):
    print(f"Index: {i}, Value: {value}")
```

---

### Important array operations

```
arr = [10, 20, 30, 40, 50]

len(arr)       # Number of elements

sum(arr)       # Sum of elements

min(arr)       # Minimum value

max(arr)       # Maximum value

any(arr)       # True if at least one is truthy

all(arr)       # True if all are truthy

sorted(arr)    # Sorted list
```

---
