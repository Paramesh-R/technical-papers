# SOLID Principles – Python Cheat Sheet

SOLID is a set of five principles used to write clean, maintainable and reusable code.

## 1. Single Responsibility Principle (SRP)

**A class should have only one responsibility.**

A class should focus on doing one particular job.

```python
# Not recommended
class Employee:
    def calculate_salary(self):
        pass

    def save_to_database(self):
        pass

    def generate_report(self):
        pass
```

Better approach:

```python
class Employee:
    def calculate_salary(self):
        pass


class EmployeeDatabase:
    def save(self, employee):
        pass


class EmployeeReport:
    def generate(self, employee):
        pass
```

**Remember:** One class = One responsibility.

## 2. Open/Closed Principle (OCP)

**Classes should be open for extension but closed for modification.**

We should be able to add new functionality without changing existing code.

```python
class EmailNotification:
    def send(self, message):
        print(f"Email: {message}")


class SMSNotification:
    def send(self, message):
        print(f"SMS: {message}")


def notify(notification, message):
    notification.send(message)


notify(EmailNotification(), "Hello")
notify(SMSNotification(), "Hello")
```

We can add new notification types without modifying the `notify()` function.

**Remember:** Extend existing functionality instead of modifying working code.

## 3. Liskov Substitution Principle (LSP)

**A child class should be usable wherever its parent class is expected.**

A child class should not break the expected behaviour of its parent.

```python
class Bird:
    def eat(self):
        print("Bird is eating")


class FlyingBird(Bird):
    def fly(self):
        print("Bird is flying")


class Sparrow(FlyingBird):
    pass


def make_bird_fly(bird):
    bird.fly()


sparrow = Sparrow()
make_bird_fly(sparrow)
```

Here, `Sparrow` can be used wherever `FlyingBird` is expected.

**Remember:** Child classes should honour the behaviour promised by their parent classes.

## 4. Interface Segregation Principle (ISP)

**A class should not be forced to implement methods it does not need.**

Instead of creating one large interface, create smaller and specific ones.

Python example:

```python
# Better approach

class Printer:
    def print_document(self):
        pass


class Scanner:
    def scan_document(self):
        pass


class MultiFunctionPrinter(Printer, Scanner):
    pass


class SimplePrinter(Printer):
    pass
```

A simple printer only implements printing. It does not need scanning functionality.

**Remember:** Keep interfaces small and specific.

## 5. Dependency Inversion Principle (DIP)

**High-level classes should not depend directly on low-level classes. Both should depend on abstractions.**

In simple terms, avoid tightly coupling classes.

```python
class EmailService:
    def send(self, message):
        print(f"Email: {message}")


class Notification:
    def __init__(self, service):
        self.service = service

    def notify(self, message):
        self.service.send(message)


email = EmailService()
notification = Notification(email)

notification.notify("Hello")
```

The `Notification` class does not create an `EmailService` object internally. It receives the service as a dependency.

We can pass another service without changing the `Notification` class.

**Remember:** Depend on abstractions, not concrete implementations.

---

## Quick Revision

| Principle | Meaning |
|---|---|
| S – SRP | One class, one responsibility |
| O – OCP | Extend without modifying existing code |
| L – LSP | Child classes should replace parent classes |
| I – ISP | Keep interfaces small and specific |
| D – DIP | Depend on abstractions, not concrete classes |

**Why SOLID?**

- Makes code easier to maintain.
- Reduces tight coupling.
- Improves code reusability.
- Makes testing easier.
- Helps when applications grow.