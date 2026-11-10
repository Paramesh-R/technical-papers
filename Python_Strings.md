# Python Strings

## Python Strings - immutable
A string (str) is a sequence of characters enclosed within single, double, or triple quotes.


```
name = "Python"
message = 'Hello World'

paragraph = """This is a
multiline string by using triple quotes"""
```

## Type Conversion - str()

The str() function converts other data types into strings
```
number = 100
price = 99.5
is_valid = True

print(str(number))   # '100'
print(str(price))    # '99.5'
print(str(is_valid)) # 'True'
```

## String Indexing
Strings are ordered
Characters keep their position, so I can access them using an index.
```
word = "Python"
print(word[0])  # P
print(word[1])  # y
```
Positive indexing (left to right):
Character	P	y	t	h	o	n
Index	0	1	2	3	4	5

Negative indexing (right to left):
Character	P	y	t	h	o	n
Index	-6	-5	-4	-3	-2	-1

Examples:
```
print(text[0])   # P
print(text[2])   # t
print(text[-1])  # n
print(text[-2])  # o
```






## Immutable:
- Strings are immutable
- Once a string is created, its individual characters cannot be changed.
```
word = "Python" 
word[0] = "J"  # TypeError

#I can create a new string instead:

word = "J" + word[1:]
print(word)  # Jython
```

## Slicing
  Slicing is used to extract a portion of a string.
  '''
  string[start:stop:step]
  '''
  - start – Starting index (included).
  - stop – Ending index (excluded).
  - step – Number of positions to skip.


## String Operators
Python supports several operators to work with strings.
|Operator	|Description|	Example|	Output|
|---|-------------|--------|------------|
|+	|Concatenation	|"Py" + "thon"|	Python|
|*	|Repetition	|"Hi " * 3	|Hi Hi Hi|
|in	|Checks existence|	"Py" in "Python"	|True|
|not| in	Checks absence|	"Java" not in "Python"|	True|
|==	|Equality	|"abc" == "abc"|	True|
|!=|	Inequality	|"abc" != "xyz"|	True|

## String Methods – Case Conversion
 Python provides built-in methods to change the case of a string.
|
||
|Method|	Description	|Example|	Output|
|------|--------------|-------|------|
|upper()	|Converts to uppercase	|"hello".upper()	|HELLO|
|lower()	|Converts to lowercase	|"HELLO".lower()	|hello|
|title()	|Capitalizes each word	|"hello world".title()	|Hello World|
|capitalize()|Capitalizes first character	|"hello world".capitalize()	|Hello world|
|swapcase()	|Reverses character cases	|"Hello".swapcase()	|hELLO|
|casefold()	|Strong lowercase conversion for comparisons	|"HELLO".casefold()	|hello|

## Removing Spaces and Characters
Python provides methods to remove unwanted characters from the beginning and end of a string.
|Method	|Description|
|--------|-----------|
|strip()|	Removes characters from both ends|
|lstrip()|	Removes characters from the left|
|rstrip()|	Removes characters from the right|

```
text = "  Hello Python  "

print(text.strip())   # "Hello Python"
print(text.lstrip())  # "Hello Python  "
print(text.rstrip())  # "  Hello Python"
```
## Removing Specific Characters
```
text = "---Python---"

print(text.strip("-"))   # Python
print(text.lstrip("-"))  # Python---
print(text.rstrip("-"))  # ---Python
```

## Searching and Counting
Python provides methods to search for substrings and count their occurrences.

|Method|	Description|
|-------|------------|
|find()	|Returns the first matching index; -1 if not found|
|index()|	Returns the first matching index; raises ValueError if not found|
|count()|	Counts occurrences of a substring|
|startswith()	|Checks whether a string starts with a value|
|endswith()	|Checks whether a string ends with a value|

Examples:
```
text = "banana"

print(text.find("na"))       # 2
print(text.index("na"))      # 2
print(text.count("a"))       # 3
print(text.startswith("ban")) # True
print(text.endswith("na"))   # True

print(text.find("xyz"))      # -1
# print(text.index("xyz"))   # ValueError
```
## Replacing and Splitting Strings

- replace() - Replaces a specific substring with another substring.
  
  Syntax: string.replace(old, new, count*)
    - count : is optional and specifies the maximum number of replacements.
  ```
  text = "I like Java"

  print(text.replace("Java", "Python"))
  # I like Python
  ```
- split(seperator=" ") -Split a string into a list based on a separator.
  
  ```
  text = "Python,Java,C++"

  print(text.split(","))
  # ['Python', 'Java', 'C++']

  ```

  - join() : combines elements of an iterable into a single string using a separator
  
  ```
    words = ["Learn", "Python", "Programming"]

    print(" ".join(words))
    # Learn Python Programming

    print("-".join(words))
    # Learn-Python-Programming
  ```
## String Checking Methods

|Method	|Description	|Example	|Output|
|-|-|-|-|
|isalpha()	|Checks whether all characters are alphabets	|"Hello".isalpha()	|True|
|isdigit()	|Checks whether all characters are digits	|"123".isdigit()	|True|
|isalnum()	|Checks whether all characters are letters or digits	|"abc123".isalnum()	|True|
|isspace()	|Checks whether all characters are whitespace	|"  ".isspace()	|True|
|islower()	|Checks whether all cased characters are lowercase	|"hello".islower()	|True|
|isupper()	|Checks whether all cased characters are uppercase	|"HELLO".isupper()	|True|
|istitle()	|Checks title case	|"Hello World".istitle()	|True|
|isidentifier()	|Checks whether the string is a valid Python identifier	"my_var".isidentifier()	|True|


## String Formatting
  String formatting is used to insert variables or expression into a string

  - ### f-strings (Recommended)
    Use f before the string and place variables inside {}.
    ```
    name = "Python"version = 3.14
    print(f"Learning {name} version {version}")
    # Learning Python version 3.14
    ```

---
  - ### format() method
    Uses {} as placeholders.
    
    ```
    name = "Python"

    print("Learning {}".format(name))
    # Learning Python
    ```

  ---
  - ### % formatting (Older approach)
    ```
      name = "Python"
      age = 10

      print("Name: %s, Age: %d" % (name, age))
    ```


---
## Escape Characters and Raw Strings

  Special characters represented using a backslash (\).

    - Escape sequences start with \
    - Raw strings are useful for file path and regular expressions
    - A raw string cannot end with a single backslash

  |Escape	|Description	|Example|
  |---| --------------|-------|
  |\n	| New line	|"Hello\nWorld"|
  |\t	| Tab space	"|Hello\tWorld"|
  |\\	| Backslash	|"C:\\Python"|
  |\'	| Single quote	|'It\'s Python'|
  |\"	| Double quote	|"He said \"Hello\""|
  |\r	| Carriage return	|"Hello\rWorld"|
  |\b	| Backspace	|"Hello\b"|

  ### Raw strings (r)

  Raw strings treat backslashes as literal characters instead of interpreting them as escape sequences.
  ```
    path = r"C:\Users\Python\Documents"

    print(path)
    # C:\Users\Python\Documents
  ```
  ---
  ## Useful Built-in Functions for Strings
|Function|Description	|Example	|Output|
|----------|----------|----------|----------|
|len()	|Returns string length	|len("Python")|	6|
|min()	|Returns smallest character	|min("cab")	|'a'|
|max()	|Returns largest character|	max("cab")	|'c'|
|sorted()	|Returns sorted characters as a list	|sorted("cab")|	['a', 'b', 'c']|
|ord()	|Converts character to Unicode number|	ord("A")|	65|
|chr()	|Converts Unicode number to character	|chr(65)	|'A'|



## String Immutability
Strings in Python are immutable, which means their contents cannot be modified after creation.

```
  text = "Python"

  # This will raise TypeError
  text[0] = "J"
```

Important points
- Strings cannot be modified in place.
- String methods return new strings.
- The original string remains unchanged unless you reassign the variable.
- Repeated string concatenation inside loops can be inefficient.
- Use join() when combining many strings.


## String Iteration
Iteration means accessing each character of a string one by one.
1. Using for loop
```
text = "Python"
for char in text:    
    print(char)
```


Output:
P
y
t
h
o
n


2. Using range() and indexing
text = "Python"for i in range(len(text)):    print(i, text[i])



3. Using enumerate()
enumerate() provides both index and character during iteration.
text = "Python"for index, char in enumerate(text):    print(index, char)



Output:
0 P
1 y
2 t
3 h
4 o
5 n


Important points:
- for loop directly accesses each character.
- range() is useful when the index is required.
- enumerate() provides index and value together.
- Strings are iterable.