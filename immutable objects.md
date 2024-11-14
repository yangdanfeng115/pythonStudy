In Python, immutable objects are objects whose value cannot be changed after they are created. If you attempt to modify an immutable object, a new object is created instead of modifying the original object.

# Key Characteristics of Immutable Objects: 
## Cannot be changed:

Once an immutable object is created, its state cannot be changed.

## Re-assignment creates new objects:

Any operation that seems to change an immutable object will create a new object instead of modifying the existing one.

## Hashable:

Immutable objects can be used as keys in dictionaries or elements in sets because they have a fixed hash value.

## Common Immutable Objects in Python: 
Integers
Floats
Strings
Tuples
Frozen Sets
Bytes

### 1. Integers (and other numeric types) 

Integers are immutable. When you modify the value of an integer, Python creates a new object with the new value.

Example:

```python

a = 5
b = a  # a and b both reference the integer 5

a = 10  # Now a refers to a new integer object with value 10
print(a)  # Output: 10
print(b)  # Output: 5

```

In this example:

a initially refers to the integer 5, and b also references the same integer object.
When a = 10 is executed, Python creates a new integer object with value 10 and rebinds a to this new object. b still references the original integer 5.

### 2. Strings 

Strings are immutable. Any operation that modifies a string, like concatenation or slicing, will create a new string.

```python

s = "hello"
s = s + " world"  # A new string is created, s now refers to "hello world"
print(s)  # Output: "hello world"

```
s originally refers to the string "hello".
When s = s + " world" is executed, a new string "hello world" is created, and s now refers to that new string.

### 3. Tuples 

Tuples are immutable. You cannot modify their elements or change their size once they are created.

```python

t = (1, 2, 3)
#Attempting to modify a tuple will result in an error
#t[1] = 4  # TypeError: 'tuple' object does not support item assignment

```

However, you can rebind a variable to a new tuple:

```python

t = (1, 2, 3)
t = (4, 5, 6)  # This creates a new tuple and binds t to it
print(t)  # Output: (4, 5, 6)

```

### 4. Frozen Sets

A frozenset is an immutable version of a set. Once created, its contents cannot be changed.

``` python

frozen_set = frozenset([1, 2, 3])
#frozen_set.add(4)  # AttributeError: 'frozenset' object has no attribute 'add'

```

Once a frozenset is created, you cannot add or remove elements from it. But you can rebind it to a new frozenset:

```python

frozen_set = frozenset([1, 2, 3])
frozen_set = frozenset([4, 5, 6])  # Creates a new frozenset
print(frozen_set)  # Output: frozenset({4, 5, 6})

```

### 5. Bytes

bytes objects in Python are immutable sequences of bytes, unlike bytearray, which is mutable.

``` python

b = b'hello'
#b[0] = 72  # TypeError: 'bytes' object does not support item assignment

```
You cannot modify individual bytes in a bytes object. If you want to change a bytes object, you need to create a new bytes object:

```python

b = b'hello'
b = b'world'  # A new bytes object is created
print(b)  # Output: b'world'

```

# Why are Immutable Objects Important?

## Thread safety: 

Immutable objects are inherently thread-safe because their state cannot be modified, so multiple threads can access them without risk of changing their value concurrently.

## Hashable: 

Immutable objects can be used as keys in dictionaries and elements in sets, since their hash values are guaranteed to remain constant.

## Performance: 

Since immutable objects cannot change, Python can optimize memory usage by reusing objects in certain situations, such as with small integers or strings.

# Summary of Immutable Objects:


# How Immutable Objects Behave

If you modify an immutable object, a new object is created with the new value, leaving the original object unchanged.
This is different from mutable objects (like lists, dictionaries, and sets), where changes to an object affect the original object in place.
Example of Immutable and Mutable Objects

```python

#Immutable: Integers
x = 10
y = x  # y refers to the same object as x
x = 20  # New object created for x
print(x)  # Output: 20
print(y)  # Output: 10

#Mutable: List
a = [1, 2, 3]
b = a  # b refers to the same list as a
a.append(4)  # Changes the original list
print(a)  # Output: [1, 2, 3, 4]
print(b)  # Output: [1, 2, 3, 4]

```

In the first case, integers are immutable, so modifying x creates a new object, and y still refers to the original object. In the second case, lists are mutable, so modifying the list a affects both a and b since they reference the same list.

# Conclusion
Immutable objects are fundamental in Python and play a key role in the design and performance of Python programs. Understanding how they work helps you avoid unintended side effects when working with variables and allows you to leverage Python's optimizations for immutable types.
