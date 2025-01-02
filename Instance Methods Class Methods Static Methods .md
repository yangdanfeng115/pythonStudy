# 1. Instance Methods

## When to Use:
When the behavior depends on the specific instance's state (i.e., instance variables).
When you need to interact with other instance-specific methods or data.

## Use Cases:
Modifying or accessing instance attributes.
Implementing behaviors unique to a particular instance.

``` python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance  # Instance attribute

    def deposit(self, amount):
        self.balance += amount

    def withdraw(self, amount):
        if self.balance >= amount:
            self.balance -= amount
        else:
            raise ValueError("Insufficient funds")

account = BankAccount(100)
account.deposit(50)
print(account.balance)  # Output: 150

``` 
# 2. Class Methods

## When to Use:
When the behavior is relevant to the class as a whole, not a specific instance.
When you need to create an alternate constructor (a method to create instances in a different way).
When you need to modify or access class variables.

## Use Cases:
Factory methods or alternate constructors.
Managing or interacting with class-level state.
```python
class Employee:
    company_name = "TechCorp"  # Class variable

    def __init__(self, name):
        self.name = name

    @classmethod
    def set_company_name(cls, new_name):
        cls.company_name = new_name

    @classmethod
    def from_string(cls, employee_str):
        name = employee_str.split("-")[0]
        return cls(name)

# Using class methods
Employee.set_company_name("NewTech")
print(Employee.company_name)  # Output: NewTech

# Alternate constructor
emp = Employee.from_string("Alice-123")
print(emp.name)  # Output: Alice

```

# 3. Static Methods

## When to Use:
When the method doesn’t interact with instance or class-level state.
When the method provides utility or helper functionality relevant to the class, but it doesn't need to know about specific instances or the class itself.
## Use Cases:
Utility or helper functions (e.g., validations, calculations).
Functions that logically belong to the class but don’t operate on its state.

```python

class MathUtils:
    @staticmethod
    def add_numbers(a, b):
        return a + b

    @staticmethod
    def is_even(number):
        return number % 2 == 0

# Using static methods
print(MathUtils.add_numbers(3, 5))  # Output: 8
print(MathUtils.is_even(10))       # Output: True

```

