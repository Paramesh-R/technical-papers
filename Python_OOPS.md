# Python OOPS

OOP stands for Object-Oriented Programming.

It is a programming approach where we organize our code using Classes and Objects.

Instead of writing all our code in separate functions, we group related data and functions together.


## Four main pillars of OOP
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction

## Important advantages of OOP
1. Code Reusability – Reuse existing code.
2. Maintainability – Easier to modify and manage code.
3. Modularity – Divide large applications into smaller components.
4. Scalability – Easier to extend applications.
5. Data Protection – Control how data is accessed and modified.
   
## Class and Object in Python
### What is a Class?

A class is a blueprint or template used to create objects.

It defines:
- What data an object can have.
- What actions an object can perform.3

Real-world example:

Imagine a house construction plan.
- Blueprint → Class
- Actual house → Object

Using the same blueprint, we can construct multiple houses.

Similarly, using one Python class, we can create multiple objects.

Syntax:
```
    class ClassName:
        # attributes
        # methods
```
---
### What is an Object?

An object is an instance of a class.

We create an object by calling the class name.

    class Student:
            name = "John"
            age = 25


        student1 = Student()
        student2 = Student()

Here:
- Student – Class.
- student1 – First object.
- student2 – Second object.
Both objects are created using the same class.

---
Accessing Class Attributes
    We can access attributes using the dot (.) operator.

   
        class Student:
        name = "John"
        age = 25


        student1 = Student()

        print(student1.name)
        print(student1.age)
   
---
#### Creating Multiple Objects
```
class Student:
    name = "John"
    age = 25


student1 = Student()
student2 = Student()

print(student1.name)    # John
print(student2.name)    # John
```

---
### Important terms to remember
|Term|	Meaning|
|------|------------|
|Class|	Blueprint for creating objects|
|Object|	Instance of a class|
|Attribute|	Data associated with a class or |object
|Method|	Function defined inside a class|
|Instance|	Another term for an object|

---

## Attributes and Methods in Python
class is a blueprint.
object is an instance of that class.

Now let's understand two important building blocks of a class:
1. Attributes – What an object has (data).
2. Methods – What an object can do (behaviour).

### What are Attributes?
Attributes are variables associated with a class or an object.

They store information about an object.

Example:

Consider a car. It has:
- Brand
- Model
- Colour
- Speed
- 
These are its attributes.

    ```
    class Car:
        brand = "Toyota"
        model = "Innova"
        color = "White"
        speed = 120
    ```

---
### What are Methods?
Methods are functions defined inside a class.

They represent the actions an object can perform.

Example:

A car can:
- Start
- Stop
- Accelerate
- Brake

These are its behaviours.
```
    class Car:

        def start(self):
            print("Car started")

        def stop(self):
            print("Car stopped")

        def accelerate(self):
            print("Car is accelerating")


    car1 = Car()

    car1.start()        # Car started
    car1.stop()         # Car stopped
    car1.accelerate()   # Car is accelerating


```

Combining Attributes and Methods:

    ```
    class Car:

        brand = "Toyota"
        model = "Innova"

        def start(self):
            print(f"{self.brand} started")

        def stop(self):
            print(f"{self.brand} stopped")


    car1 = Car()

    print(car1.brand)
    print(car1.model)

    car1.start()
    car1.stop()
    ```

---
## CONSTRUCTOR
### What is a Constructor?

A Constructor is commonly described as a special method used to initialize an object when it is created.



SYNTAX:
```
class ClassName:

    def __init__(self):
        # Initialization code
        pass
```

    - __init__() initializes an object; 

    - it does not create the object itself. 

    - Object creation is handled by __new__().

Example - Usage:
```
    class Student:

        def __init__(self, name, age = 18):
            self.name = name
            self.age = age


    student1 = Student("John", 25)
    student2 = Student("David", 22)

    print(student1.name)   # John     
    print(student1.age)    # 25 

    print(student2.name)   # David     
    print(student2.age)    # 22
```

|Constructor (__init__)	|Normal Method|
|---------- |------------|
|Initializes an object	|Performs a specific operation|
|Called automatically during object initialization	|Called explicitly|
|Conventionally named __init__	|Can have any valid method name|
|Usually initializes attributes	|Usually implements behaviour|

---
## self Keyword in Python

What is self?

self refers to the current object (instance) of a class.

It allows us to access the attributes and methods belonging to that particular object.

Python automatically passes the current object as the first argument when calling an instance method through an object.

    class Student:

        def __init__(self, name, age):
            self.name = name
            self.age = age

        def display(self):
            print(self.name, self.age)


    student1 = Student("John", 25)
    student2 = Student("David", 22)

    student1.display()
    student2.display()


    Notice:
- When student1.display() is called, self refers to student1.
- When student2.display() is called, self refers to student2.


---
## Instance Methods, Class Methods and Static Methods

In Python, methods are functions defined inside a class.

Python provides three commonly used types of methods:
1. Instance Methods
2. Class Methods
3. Static Methods
Let's understand each one with simple examples.



### Instance Methods
An instance method works with the data of a particular object.
- It uses self as its first parameter.
- It can access instance attributes.
- It can also access class attributes.

```
class Employee:

    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def display_details(self):
        print(self.name)
        print(self.salary)


emp1 = Employee("John", 50000)
emp2 = Employee("David", 60000)

emp1.display_details()
emp2.display_details()
```

```
John
50000
David
60000
```


Notice that the same method works with different objects and accesses their respective data.

When to use: When a method needs to access or modify an object's data.





### Class Methods
A class method works with the class itself rather than a particular object.
- It uses cls as its first parameter.
- It is defined using @classmethod.
- It can access and modify class attributes.
- It can also be used as an alternative constructor.
Example:
```
    class Employee:    
        company = "TCS"    

        @classmethod    
        def change_company(cls, new_company):        
            cls.company = new_company


    emp1 = Employee()
    emp2 = Employee()


    Employee.change_company("Infosys")


    print(emp1.company)
    print(emp2.company)
```

```
    # Output:
    Infosys
    Infosys
```
## Instance Variables vs Class Variables

-   **Instance variable:** Belongs to one object. Usually created with
    `self`.
-   **Class variable:** Shared through the class by its instances.
    Defined in the class body.

``` python
class Employee:
    company = "ABC"                 # class variable

    def __init__(self, name):
        self.name = name            # instance variable

e1 = Employee("Ana")
e2 = Employee("Ben")

e1.name = "Anita"                   # changes only e1
Employee.company = "XYZ"            # changes class value
```

**Important:** Avoid changing a mutable class variable through an
instance. A shared list or dictionary can unexpectedly be changed by
every object.

``` python
class Team:
    members = []                    # shared list — usually a mistake
```

Prefer creating per-object mutable data in `__init__`:

``` python
class Team:
    def __init__(self):
        self.members = []
```




## 8. Accessing and Modifying Attributes

Use dot notation to read or assign attributes.

``` python
class Person:
    def __init__(self, name):
        self.name = name

p = Person("Maya")
print(p.name)
p.name = "Mira"
```

Useful built-ins:

``` python
hasattr(p, "name")                  # attribute exists?
getattr(p, "name", "Unknown")       # read with fallback
setattr(p, "name", "Maya")          # assign
delattr(p, "name")                  # delete
```

**Remember:** `obj.attribute` is ordinary attribute access; properties
and descriptors can customize what happens behind it.

## 9. Constructors: Default and Variable Arguments

`__init__` initializes a newly created object. It is not the method that
creates the object; `__new__` does that.

``` python
class User:
    def __init__(self, name, active=True):
        self.name = name
        self.active = active

u1 = User("Sam")
u2 = User("Lee", False)
```

Variable arguments:

``` python
class Report:
    def __init__(self, title, *items, **options):
        self.title = title
        self.items = items
        self.options = options

r = Report("Sales", "Jan", "Feb", format="csv")
```

**Important:** Do not use mutable defaults such as `items=[]`. Use
`None` and create a new list inside the method.

## 10. Method Types --- Quick Revision

``` python
class Example:
    count = 0

    def instance_method(self):
        return self.count            # works with an object

    @classmethod
    def class_method(cls):
        cls.count += 1               # works with the class

    @staticmethod
    def is_valid(value):
        return value > 0             # no automatic self or cls
```

  -----------------------------------------------------------------------
  Type                    First automatic         Typical use
                          argument                
  ----------------------- ----------------------- -----------------------
  Instance method         `self`                  Read/change one
                                                  object's state

  Class method            `cls`                   Work with class state;
                                                  alternative
                                                  constructors

  Static method           None                    Related utility that
                                                  needs no object/class
                                                  state
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# Encapsulation

## Encapsulation

**Meaning:** Keep related data and methods together, and control how the
object's data is accessed or changed.

``` python
class BankAccount:
    def __init__(self, balance):
        self._balance = balance

    def deposit(self, amount):
        if amount > 0:
            self._balance += amount
```



## Public, Protected and Private Names

Python uses naming conventions rather than strict access modifiers.

``` python
class Example:
    def __init__(self):
        self.name = "Public"
        self._status = "Internal use by convention"
        self.__pin = 1234
```

  |Style     | Meaning|
  |---------- |--------------------------------------------|
  |`name`     |Public; normal access|
  |`_name`    |Non-public by convention; still accessible|
  |`__name`   |Name-mangled to reduce accidental clashes|

**Important:** A single underscore does not enforce protection. Double
underscore is not true security or absolute privacy.

## Name Mangling

A name such as `self.__pin` is internally rewritten approximately as
`_ClassName__pin`.

``` python
class Account:
    def __init__(self):
        self.__pin = 1234

a = Account()
# a.__pin                 # AttributeError
print(a._Account__pin)    # technically accessible; avoid relying on it
```

**Why?** Mainly to avoid accidental name clashes in subclasses, not to
hide secrets.

## Getters and Setters

Methods can validate data before returning or changing it.

``` python
class Product:
    def __init__(self, price):
        self._price = price

    def get_price(self):
        return self._price

    def set_price(self, value):
        if value < 0:
            raise ValueError("Price cannot be negative")
        self._price = value
```

Python often uses `@property` for a cleaner interface.

## `@property`

A property lets a method be accessed like an attribute.

``` python
class Product:
    def __init__(self, price):
        self.price = price          # uses the setter

    @property
    def price(self):
        return self._price

    @price.setter
    def price(self, value):
        if value < 0:
            raise ValueError("Price cannot be negative")
        self._price = value

p = Product(100)
p.price = 150
print(p.price)
```

-   `@property`: getter
-   `@name.setter`: setter
-   `@name.deleter`: optional deleter

**Use it when:** Reading or assigning an attribute needs validation or
calculated behaviour.

------------------------------------------------------------------------

# Inheritance

## Inheritance

A child class can reuse and extend a parent class.

``` python
class Animal:
    def eat(self):
        print("Eating")

class Dog(Animal):
    def bark(self):
        print("Barking")

dog = Dog()
dog.eat()
dog.bark()
```

**Use it when:** There is a genuine "is-a" relationship and the child
can correctly behave as the parent.

## Single Inheritance

One child inherits from one parent.

``` python
class Vehicle:
    def start(self):
        print("Started")

class Car(Vehicle):
    pass
```

## Multiple Inheritance

One child inherits from multiple parents.

``` python
class Camera:
    def take_photo(self):
        print("Photo")

class Phone:
    def call(self):
        print("Calling")

class SmartPhone(Camera, Phone):
    pass
```

**Caution:** Multiple inheritance can make method lookup and design
harder. Use it thoughtfully.

## Multilevel Inheritance

Inheritance forms a chain.

``` python
class LivingThing:
    pass

class Animal(LivingThing):
    pass

class Dog(Animal):
    pass
```

## Hierarchical Inheritance

Multiple child classes inherit from one parent.

``` python
class Animal:
    def eat(self):
        print("Eating")

class Dog(Animal):
    pass

class Cat(Animal):
    pass
```

## Hybrid Inheritance

A combination of two or more inheritance patterns. Python uses Method
Resolution Order (MRO) to decide where methods are found.

``` python
class A: pass
class B(A): pass
class C(A): pass
class D(B, C): pass
```

## `super()`

`super()` delegates a method call to the next class in the Method
Resolution Order.

``` python
class Person:
    def __init__(self, name):
        self.name = name

class Employee(Person):
    def __init__(self, name, salary):
        super().__init__(name)
        self.salary = salary
```

**Important:** In multiple inheritance, `super()` follows the MRO; it
does not simply mean "call my direct parent".

## Method Overriding

A child class provides its own implementation of an inherited method.

``` python
class Animal:
    def speak(self):
        print("Some sound")

class Dog(Animal):
    def speak(self):
        print("Woof")
```

Use `super().method()` when the child should extend the parent
implementation.

## Method Resolution Order (MRO)

MRO is the order Python follows to find a method or attribute in an
inheritance hierarchy.

``` python
class A: pass
class B(A): pass
class C(A): pass
class D(B, C): pass

print(D.mro())
# D -> B -> C -> A -> object
```

Python uses C3 linearization to create a consistent MRO.

**Useful checks:** `ClassName.mro()` and `ClassName.__mro__`.

------------------------------------------------------------------------

# Polymorphism

## Polymorphism

**Meaning:** The same operation or interface can work with different
object types.

``` python
class Dog:
    def speak(self):
        return "Woof"

class Cat:
    def speak(self):
        return "Meow"

def make_sound(animal):
    print(animal.speak())

make_sound(Dog())
make_sound(Cat())
```

## Duck Typing

Python often cares about what an object can do, rather than its exact
class.

``` python
class FileLike:
    def read(self):
        return "data"

class NetworkStream:
    def read(self):
        return "network data"

def process(source):
    print(source.read())
```

If an object supports the required operation, it can be used.

## Overriding and Polymorphism

Overriding is one way to achieve runtime polymorphism: different
subclasses implement the same method differently.

``` python
class Shape:
    def area(self):
        raise NotImplementedError

class Square(Shape):
    def __init__(self, side):
        self.side = side

    def area(self):
        return self.side ** 2
```

For a formal contract, consider an abstract base class.

## Operator Overloading

Special methods let custom objects work with operators.

``` python
class Point:
    def __init__(self, x, y):
        self.x, self.y = x, y

    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)

p3 = Point(1, 2) + Point(3, 4)
print(p3.x, p3.y)                   # 4 6
```

Common examples: `__add__`, `__sub__`, `__eq__`, `__lt__`, `__mul__`.

## Method Overloading Alternatives

Python does not support traditional signature-based method overloading
in the same way as Java or C++: a later method definition replaces an
earlier one.

Common alternatives:

``` python
class Greeter:
    def greet(self, name="there"):
        print(f"Hello, {name}")

g = Greeter()
g.greet()
g.greet("Maya")
```

Other options include `*args`, `**kwargs`, default arguments, and
`functools.singledispatch` for type-based function dispatch.

------------------------------------------------------------------------

# Abstraction

## Abstraction

**Meaning:** Expose what an object can do while hiding the details of
how it does it.

Example: A user calls `payment.pay()` without needing to know the
internal payment-processing steps.

## Abstract Classes, Abstract Methods and `abc`

Use Python's `abc` module to define a contract that subclasses must
implement.

``` python
from abc import ABC, abstractmethod

class Payment(ABC):
    @abstractmethod
    def pay(self, amount):
        pass

class CardPayment(Payment):
    def pay(self, amount):
        print(f"Paid {amount} by card")

payment = CardPayment()
payment.pay(500)
```

-   `ABC`: Base class for abstract classes.
-   `@abstractmethod`: Marks a method that concrete subclasses must
    implement.
-   An abstract class with unimplemented abstract methods cannot be
    instantiated.

## Interface-like Design in Python

Python does not have a separate `interface` keyword. Interface-like
contracts can be created using:

-   Abstract Base Classes (`abc`) for explicit runtime contracts.
-   `typing.Protocol` for structural, static type checking.

``` python
from typing import Protocol

class Printable(Protocol):
    def print_data(self) -> None:
        ...

def print_item(item: Printable):
    item.print_data()
```

A class can satisfy a protocol by providing the required method, without
inheriting from it.

------------------------------------------------------------------------

# Relationships Between Classes

## Association

Two independent objects know about or work with each other.

``` python
class Teacher:
    def teach(self, student):
        print("Teaching", student.name)

class Student:
    def __init__(self, name):
        self.name = name
```

## Aggregation

A "has-a" relationship where the contained object can exist
independently of the container.

``` python
class Department:
    def __init__(self, employees):
        self.employees = employees   # supplied from outside
```

The employees can exist even if the department object is removed.

## Composition

A strong ownership relationship where the containing object creates and
manages its component objects.

``` python
class Engine:
    pass

class Car:
    def __init__(self):
        self.engine = Engine()
```

The example shows ownership in code; Python does not enforce object
lifetime dependency.
