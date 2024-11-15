# Reference Counting

When an object is created, a reference is made to that object, and when it is no longer needed, i.e., when an object's refcount goes down to zero, it is garbage-collected. (This is not 100 percent true, but 
pretend it is for now.)

# Incrementing the Reference Count

The refcount for an object is initially set to 1 when an object is created and (its reference) assigned.New references to objects, also called aliases, occur when additional variables are assigned to the same 
object, passed as arguments to invoke other bodies of code such as functions, methods, or class instantiation, or assigned as members of a sequence or mapping.
Let us say we make the following declarations:

 x = 3.14
 
 y = x
 
The statement x = 3.14 allocates a floating point number (float) object and assigns a reference x to it. xis the first reference, hence setting that object's refcount to one. The statement y = x creates an alias y, 
which "points to" the same integer object as x . A new object is not created for y.

![immutable](https://github.com/yangdanfeng115/pythonStudy/blob/main/images/An%20object%20with%20two%20references.png)

Instead, the only thing that happens is that the reference count for this object is incremented by one (to 2). This is one way in which an object's refcount goes up. Other ways it can increment include the object 
being passed into a function call, and when the object is added to a container object such as a list. 

## In summary, an object's refcount is increased when

● It (the object) is created
 x = 3.14
 
● Additional aliases for it are created
 y = x
 
● It is passed to a function (new local reference)
 foobar(x)
 
● It becomes part of a container object
 myList = [123, x, 'xyz']

# Decrementing the Reference Count

When references to an object "go away," the refcount is decreased. The most obvious case is when a reference goes out of scope. This occurs most often when the function in which a reference is made 
completes. The local (automatic) variable is gone, and an object's reference counter is decremented.A reference also goes away when a variable is reassigned to another object. For example:

 foo = 'xyz'
 
 bar = foo
 
 foo = 123
 
The reference count for string object "xyz" is one when it is created and assigned to foo. It is then incremented when bar is added as an alias. However, when foo is reassigned to the integer 123, the reference count to "xyz" is decremented by one. Other ways in which an object's reference count goes down include explicit removal of a reference using the del statement (see next section), when an object is removed from a container (or if the reference 
count to that container itself goes to zero).

## In summary, an object's refcount is decreased when:

● A local reference goes out of scope, i.e., when foobar() (see previous example) terminates

● Aliases for that object are explicitly destroyed
 del y # or del x
 
● An alias is reassigned to another object (taking on a new reference)
 x = 123
 
● It is explicitly removed from a container object
 myList.remove(x)
 
● The container itself is deallocated
 del myList # or goes out-of-scope
