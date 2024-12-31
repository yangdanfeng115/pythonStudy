Why the last output is as below?

3.0
2.0
3.0

# Code Behavior Analysis:

## Class Variable Declaration:

raise_amount is initially a class variable shared among all instances (emp_1, emp_2) and the class itself (Employee).

## Instance Variable Assignment:

When you execute emp_1.raise_amount = 2.0, Python creates a new instance variable raise_amount specific to emp_1.
This instance variable shadows the class variable raise_amount for emp_1, meaning that emp_1.raise_amount now refers to its own instance variable, not the class variable.
However, emp_2.raise_amount and Employee.raise_amount still refer to the shared class variable.

## Class Variable Update:

When you execute Employee.raise_amount = 3.0, the class variable raise_amount is updated to 3.0.
This update affects the class variable itself and any instances that still rely on the class variable (e.g., emp_2).
Since emp_1 already has its own instance-specific raise_amount, it remains unaffected by this change.

# Key Concepts in Action:
## Instance Variable Shadows Class Variable:

When emp_1.raise_amount = 2.0 is executed, Python creates a new instance variable raise_amount for emp_1, which shadows the class variable.
## Class Variable Update:

Updating Employee.raise_amount = 3.0 changes the value of the class variable.
Any instance that does not have an instance-specific raise_amount will see this updated value.

## Separate Namespace for Instance Variables:

Each instance has its own namespace. When you create emp_1.raise_amount, it exists only in emp_1's namespace, separate from the class namespace.

```python

class Employee:
    number_of_emps = 0
    raise_amount = 1.04

    def __init__(self, first, last, pay):
        self.first = first
        self.last = last
        self.pay = pay
        self.email = first + '.' + last + '@company.com'

        Employee.number_of_emps += 1

    def fullname(self):
        return '{} {}'.format(self.first, self.last)

    def apply_raise(self):
        self.pay = int(self.pay * self.raise_amount)


emp_1 = Employee('Dafei', 'Tao', 50000)
emp_2 = Employee('Lili', 'Liu', 30000)

print(Employee.raise_amount)
print(emp_1.raise_amount)
print(emp_2.raise_amount)
print(emp_1.__dict__)
print(emp_2.__dict__)
print(Employee.__dict__)


#change instance emp_1 variable
emp_1.raise_amount = 2.0
print(Employee.raise_amount)
print(emp_1.raise_amount)
print(emp_2.raise_amount)
print(emp_1.__dict__)
print(emp_2.__dict__)
print(Employee.__dict__)


#change class variable
Employee.raise_amount = 3.0
print(Employee.raise_amount)
print(emp_1.raise_amount)
print(emp_2.raise_amount)
print(emp_1.__dict__)
print(emp_2.__dict__)
print(Employee.__dict__)


Output:

1.04
1.04
1.04
{'first': 'Dafei', 'last': 'Tao', 'pay': 50000, 'email': 'Dafei.Tao@company.com'}
{'first': 'Lili', 'last': 'Liu', 'pay': 30000, 'email': 'Lili.Liu@company.com'}
{'__module__': '__main__', '__firstlineno__': 1, 'number_of_emps': 2, 'raise_amount': 1.04, '__init__': <function Employee.__init__ at 0x000001D4A7033C40>, 'fullname': <function Employee.fullname at 0x000001D4A7038900>, 'apply_raise': <function Employee.apply_raise at 0x000001D4A7038F40>, '__static_attributes__': ('email', 'first', 'last', 'pay'), '__dict__': <attribute '__dict__' of 'Employee' objects>, '__weakref__': <attribute '__weakref__' of 'Employee' objects>, '__doc__': None}
1.04
2.0
1.04
{'first': 'Dafei', 'last': 'Tao', 'pay': 50000, 'email': 'Dafei.Tao@company.com', 'raise_amount': 2.0}
{'first': 'Lili', 'last': 'Liu', 'pay': 30000, 'email': 'Lili.Liu@company.com'}
{'__module__': '__main__', '__firstlineno__': 1, 'number_of_emps': 2, 'raise_amount': 1.04, '__init__': <function Employee.__init__ at 0x000001D4A7033C40>, 'fullname': <function Employee.fullname at 0x000001D4A7038900>, 'apply_raise': <function Employee.apply_raise at 0x000001D4A7038F40>, '__static_attributes__': ('email', 'first', 'last', 'pay'), '__dict__': <attribute '__dict__' of 'Employee' objects>, '__weakref__': <attribute '__weakref__' of 'Employee' objects>, '__doc__': None}
3.0
2.0
3.0
{'first': 'Dafei', 'last': 'Tao', 'pay': 50000, 'email': 'Dafei.Tao@company.com', 'raise_amount': 2.0}
{'first': 'Lili', 'last': 'Liu', 'pay': 30000, 'email': 'Lili.Liu@company.com'}
{'__module__': '__main__', '__firstlineno__': 1, 'number_of_emps': 2, 'raise_amount': 3.0, '__init__': <function Employee.__init__ at 0x000001D4A7033C40>, 'fullname': <function Employee.fullname at 0x000001D4A7038900>, 'apply_raise': <function Employee.apply_raise at 0x000001D4A7038F40>, '__static_attributes__': ('email', 'first', 'last', 'pay'), '__dict__': <attribute '__dict__' of 'Employee' objects>, '__weakref__': <attribute '__weakref__' of 'Employee' objects>, '__doc__': None}

进程已结束，退出代码为 0




