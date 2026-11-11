# Python Iterators and Generators

## 1. Introduction to Iteration

### What is Iteration?

Iteration is the process of accessing elements one by one from a collection.

For example:
- Accessing elements from a list.
- Reading lines from a file.
- Processing records from a database.

```python
numbers = [10, 20, 30, 40]

for number in numbers:
    print(number)
```

**Output:**
```text
10
20
30
40
```

Here, the `for` loop accesses each element one by one. This process is called iteration.

### Why do we need Iteration?

- To process data one element at a time.
- To avoid writing repetitive code.
- To handle large collections of data efficiently.

---

## 2. Iterable vs Iterator

These two terms are related but different.

### Iterable

An iterable is an object that contains elements and allows us to access them one by one.

Examples:
- List
- Tuple
- String
- Dictionary
- Set

```python
numbers = [10, 20, 30]

for number in numbers:
    print(number)
```

A list is an iterable because we can loop through its elements.

### Iterator

An iterator is an object that remembers its current position and returns the next element whenever requested.

We can create an iterator using `iter()`.

```python
numbers = [10, 20, 30]

iterator = iter(numbers)

print(next(iterator))
print(next(iterator))
print(next(iterator))
```

**Output:**
```text
10
20
30
```

### Understanding `iter()` and `next()`

| Function | Purpose |
|---|---|
| `iter()` | Creates an iterator from an iterable. |
| `next()` | Returns the next element from an iterator. |

**Important:** Once all elements are consumed, calling `next()` again raises `StopIteration`.

```python
numbers = [10, 20]

iterator = iter(numbers)

print(next(iterator))
print(next(iterator))
print(next(iterator))  # StopIteration
```

### Iterable vs Iterator

| Iterable | Iterator |
|---|---|
| Can be iterated over. | Produces elements one by one. |
| Supports `iter()`. | Supports `next()`. |
| Example: List, Tuple, String. | Example: List iterator. |
| Usually does not maintain iteration position. | Maintains current iteration position. |

---

## 3. Iterator Protocol

Python follows an internal mechanism called the Iterator Protocol.

An iterator must implement two special methods:

1. `__iter__()`
2. `__next__()`

### `__iter__()`

Returns the iterator object itself.

### `__next__()`

Returns the next element.

When there are no more elements, it must raise `StopIteration`.

### Example

```python
numbers = [10, 20, 30]

iterator = iter(numbers)

print(iterator.__iter__())
print(iterator.__next__())
print(iterator.__next__())
```

**Note:** In normal Python code, prefer `iter()` and `next()` instead of calling the special methods directly.

---

## 4. Creating a Custom Iterator

We can create our own iterator using a class.

### Example: Numbers from 1 to 5

```python
class NumberIterator:

    def __init__(self, limit):
        self.current = 1
        self.limit = limit

    def __iter__(self):
        return self

    def __next__(self):
        if self.current <= self.limit:
            number = self.current
            self.current += 1
            return number

        raise StopIteration


numbers = NumberIterator(5)

for number in numbers:
    print(number)
```

**Output:**
```text
1
2
3
4
5
```

### Explanation

- `__init__()` initializes the iterator.
- `__iter__()` returns the iterator object.
- `__next__()` provides the next number.
- `StopIteration` indicates that iteration is complete.

**Real-world usage:**

Custom iterators are useful when we want to control how data is accessed, such as:
- Reading database records in batches.
- Iterating through custom data structures.
- Processing paginated results.

---

## 5. Generators

### What is a Generator?

A generator is a special type of iterator that generates values one at a time instead of storing all values in memory.

Generators are created using functions with the `yield` keyword.

### Example

```python
def generate_numbers():
    yield 10
    yield 20
    yield 30


numbers = generate_numbers()

print(next(numbers))
print(next(numbers))
print(next(numbers))
```

**Output:**
```text
10
20
30
```

### What is `yield`?

`yield` returns a value from a generator and temporarily pauses the function's execution.

When the next value is requested, execution resumes from where it stopped.

### Difference between `return` and `yield`

| return | yield |
|---|---|
| Returns a value and ends the function. | Produces a value and pauses execution. |
| Function cannot resume from that point. | Function resumes when the next value is requested. |
| Returns a normal value. | Produces a generator object when used in a generator function. |

### Example: Understanding Execution

```python
def sample_generator():
    print("First")
    yield 10

    print("Second")
    yield 20

    print("Third")
    yield 30


generator = sample_generator()

print(next(generator))
print(next(generator))
```

**Output:**
```text
First
10
Second
20
```

Notice that the function executes only when we request values.

---

## 6. Generator Expressions

Similar to list comprehensions, Python supports generator expressions.

### List Comprehension

```python
numbers = [x * x for x in range(5)]

print(numbers)
```

Output:
```text
[0, 1, 4, 9, 16]
```

### Generator Expression

```python
numbers = (x * x for x in range(5))

print(next(numbers))
print(next(numbers))
```

Output:
```text
0
1
```

**Difference:**

- List comprehension creates and stores all elements.
- Generator expression produces elements only when requested.

---

## 7. Iterator vs Generator

| Iterator | Generator |
|---|---|
| Can be created using classes. | Created using functions with `yield`. |
| Requires implementing iterator methods for a custom iterator. | Python handles the iterator protocol automatically. |
| Can require more code. | Usually requires less code. |
| Can maintain custom iteration logic. | Automatically maintains execution state. |
| May be stateful. | Preserves local state between yields. |

**Important:** Every generator is an iterator, but not every iterator is a generator.

---

## 8. Real-world Applications

### 1. Reading Large Files

Instead of loading an entire file into memory, process it line by line.

```python
def read_file(filepath):
    with open(filepath, "r") as file:
        for line in file:
            yield line


for line in read_file("data.txt"):
    print(line)
```

**Usage:** Processing large log files.

### 2. Processing Large Datasets

Generate records one at a time instead of creating a large list.

```python
def generate_records(limit):
    for number in range(limit):
        yield {"id": number, "status": "active"}


for record in generate_records(5):
    print(record)
```

**Usage:** Database record processing and ETL pipelines.

### 3. API Pagination

Generate API pages one at a time instead of fetching all pages upfront.

**Usage:** Processing thousands of API records efficiently.

### 4. Streaming Data

Generators can produce data continuously as needed.

**Usage:** Log monitoring, event processing and data pipelines.

---

## 9. Advantages of Generators

1. Memory efficient for large sequences.
2. Lazy evaluation – values are produced only when needed.
3. Cleaner code compared to custom iterator classes.
4. Maintains execution state automatically.
5. Useful for processing streams of data.

## 10. Limitations of Generators

1. Generators are generally consumed only once.
2. Cannot directly access elements using indexes.
3. Cannot restart an exhausted generator.
4. Debugging complex generator workflows can be difficult.

---
