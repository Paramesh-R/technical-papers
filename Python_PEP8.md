# Python PEP 8 - Cheat Sheet

## What is PEP 8?

PEP 8 is the official Python coding style guide.

When followed, Python code is:

- Easy to read.
- Easy to understand.
- Consistent.
- Easy to maintain.

PEP 8 does not change how Python code works.

It helps us write clean code.

---

## Indentation

- Use 4 spaces for each indentation level.
- Do not mix tabs and spaces.
- Keep indentation consistent.

Example:

```python
if age >= 18:
    print("Adult")
    print("Eligible")
```

## Line Length

- Keep each line within 79 characters.
- Break long statements into multiple lines.
- Use parentheses when breaking long expressions.

Example:

```python
total_amount = (
    product_price
    + delivery_charge
    + tax
)
```

---

## Blank Lines

Use blank lines to separate different parts of your code.

- Use 2 blank lines between top-level functions and classes.
- Use 1 blank line between methods inside a class.
- Use blank lines to separate logical sections.

Example:

```python
def calculate_total():
    return 100


def calculate_tax():
    return 10
```

---

## Variable Names

Use `snake_case` for variable names.

- Use lowercase letters.
- Separate words using underscores.
- Choose meaningful names.

Example:

```python
student_name = "John"
total_marks = 450
employee_count = 25
```

---

## Function Names

Use `snake_case` for function names.

Example:

```python
def calculate_total_price():
    pass


def get_student_details():
    pass
```

---

## Class Names

Use `PascalCase` for class names.

Each word starts with a capital letter.

Example:

```python
class StudentDetails:
    pass


class EmployeeManagement:
    pass
```

---

## Constants

Use uppercase letters for constant names.

Separate words using underscores.

Example:

```python
PI = 3.14159
MAX_RETRY_COUNT = 5
DATABASE_NAME = "company"
```

---

## Imports

- Place imports at the beginning of the file.
- Write one import per line.
- Separate different types of imports with blank lines.

Import order:

1. Standard library imports.
2. Third-party library imports.
3. Local application imports.

Example:

```python
import csv
from pathlib import Path

import matplotlib.pyplot as plt
import pandas as pd

from utils import calculate_total
```

Avoid:

```python
import os, sys, csv
```

---

## Spaces Around Operators

Use spaces around operators.

Example:

```python
total = price + tax
average = total / count
is_valid = age >= 18
```

Avoid:

```python
total=price+tax
average=total/count
is_valid=age>=18
```

---

## Spaces After Commas

Use one space after commas.

Example:

```python
numbers = [10, 20, 30, 40]
```

---

## Avoid Unnecessary Spaces

Do not add spaces immediately inside brackets or parentheses.

Example:

```python
numbers = [10, 20, 30]
result = calculate_total(10, 20)
```

Avoid:

```python
numbers = [ 10, 20, 30 ]
result = calculate_total( 10, 20 )
```

---

## Comments

Write comments that explain why something is done.

Use complete and meaningful sentences.

Good:

```python
# Skip records without a registration date.
if not registration_date:
    continue
```

Bad:

```python
# checking date
if not registration_date:
    continue
```

---

## Docstrings

Use docstrings to explain what a function, class, or module does.

Use triple double quotes.

Example:

```python
def calculate_average(total, count):
    """Calculate the average of the given values."""
    return total / count
```

---

## Boolean Comparisons

Use simple and readable conditions.

Good:

```python
if is_active:
    print("Active")

if not is_valid:
    print("Invalid")
```

For checking `None`, use `is` or `is not`.

Example:

```python
if result is None:
    print("No result")
```

---

## String Formatting

Prefer f-strings for formatting strings.

Good:

```python
name = "John"
age = 25

print(f"My name is {name} and I am {age} years old.")
```

---

## Avoid Unnecessary Code

Write simple and readable code.

Good:

```python
if age >= 18:
    is_adult = True
else:
    is_adult = False
```

Simpler:

```python
is_adult = age >= 18
```

---

## File and Resource Handling

Use `with` when working with files.

It automatically closes the file after use.

Example:

```python
with open("data.txt", "r") as file:
    content = file.read()
```

---

## Avoid Unused Imports and Variables

Remove imports and variables that are not used.

Bad:

```python
import os
import sys

total = 100
```

If they are not used, remove them.

---

## Use a Main Function

For executable Python scripts, use a main function.

Example:

```python
def execute():
    print("Python program started")


if __name__ == "__main__":
    execute()
```

This allows the file to be imported without automatically running the program.

---

# Common Naming Conventions

| Code Element | Naming Style | Example           |
| ------------ | ------------ | ----------------- |
| Variable     | snake_case   | student_name      |
| Function     | snake_case   | calculate_total() |
| Class        | PascalCase   | StudentDetails    |
| Constant     | UPPER_CASE   | MAX_LIMIT         |
| Module       | lowercase    | calculations.py   |
| Package      | lowercase    | utilities         |

---

# PEP 8 Checking Tools

## Flake8

Flake8 checks Python code for style issues and common errors.

Install:

```bash
pip install flake8
```

Check one Python file:

```bash
flake8 main.py
```

Check the entire project:

```bash
flake8 .
```

Check with a maximum line length:

```bash
flake8 --max-line-length=79 main.py
```

## Black

Black automatically formats Python code.

Install:

```bash
pip install black
```

Format a file:

```bash
black main.py
```

Format the entire project:

```bash
black .
```

Check formatting without changing files:

```bash
black --check .
```

---
