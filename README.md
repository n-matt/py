## Object oriented concepts

### Encapsulation 
- Encapsulation is protecting properties and functionality of an object from other objects
-	Encapsulation is the process binding the methods and data/fields together so that only those methods can access that data
-	To make class variable private add double underscore to the behind the variable name
-	Private variables cannot be directly accessed through object, we get an error if we do so
-	Class level methods are needed which allow access to private variables

```
# Example 1:
class Student:
    # Initialize private class field
    def __init__(self):
       self.__id = 12

    # Class accessor method of private field
    def display(self):
       print(self.__id)

# Creating object of class
stu_obj = Student()

# Accessing private field directly does not work
# print(stu_obj.__id)   # Attribute Error

# Calling through accessor method
stu_obj.display()   # Prints 12

# Using name mangling to access private fields '_<Class_name>__<Private_field>
print(stu_obj._Student__id) # Prints 12

```

### Polymorphism
-	Polymorphism defines the ability to take different forms. Polymorphism in Python allows us to define methods in the child class with the same name as defined in their parent class
-	Duck typing is a type of polymorphism one of the features provided by dynamically typed languages like python 
-	Duck typing means that we are less concerned with the class/type of an object and more concerned with what methods can be called on it and what operations can be performed on it. We don't care about it's type, we care about what it can do

### Inheritance
-	Inheritance is the capability of one class to derive or inherit the properties from some another class
-	Python supports single, multiple and multilevel inheritance
-	We can use `super()` to invoke constructor and method of parent class
-	We can use in built issubclass() method to verify whether a particular class is a subclass of another class. Built-in function is issubclass(paramOne, paramTwo) where paramOne and paramTwo can be either class names or class's object name
-	It is recommended to call the parent class constructor from the child class

### Abstraction
-	Abstraction means hiding the complexity and only showing the essential features of the object. So in a way, Abstraction means hiding the real implementation
-	Abstraction in Python is achieved by using abstract classes and interfaces


### Immutable vs Mutable Data types
-	Immutable Objects : These are of in-built types like int, float, bool, string, unicode, tuple. In simple words, an immutable object can’t be changed after it is created
-	Mutable Objects : These are of type list, dict, set . Custom classes are generally mutable

### Deep vs Shallow copy
-	A deep copy makes a new and separate copy of an entire object or list with its own unique memory address. Any changes you make in the new copy of the object/list won't reflect in the original one. This process happens by first creating a new list or object, followed by recursively copying the elements from the original one to the new one
-	A shallow copy also makes a separate new object or list, but instead of copying the child elements to the new object, it simply copies the references to their memory addresses. Hence, if you make a change in the original object, it would reflect in the copied object, and vice versa. To put it briefly, both the copies are dependent on each other

### Decorators
A decorator is a function that takes another function and extends the behavior of the latter function without explicitly modifying it

```
def greet(func):
    def wrapper_func(*args, **kwargs):
        print("Welcome,")
        func(*args, **kwargs)
    return wrapper_func


@greet
def show_info(show_name="User"):
        print(show_name)

show_info("Username")
```

### Generators
-	There is a lot of work in building an iterator in Python. We have to implement a class with `__iter__()` and `__next__()` method, keep track of internal states, and raise StopIteration exception, when there are no values to be returned
-	Python generators are a simple way of creating iterators. All the work we mentioned above are automatically handled by generators in Python.
-	Simply speaking, a generator is a function that returns an object (iterator) which we can iterate over (one value at a time)
-	It is fairly simple to create a generator in Python. It is as easy as defining a normal function, but with a yield statement instead of a return statement
-	yield statement pauses the function saving all its states and later continues from there on successive calls
-	The major advantage is less memory consumption

### Abstract Base Class
-	An abstract method is simply a method that is declared, but contains no implementation (not decorated)
-	Interfaces are abstract classes which have only abstract method to enforce a contract in the child classes
-	Abstract classes are classes that contain one or more abstract methods
-	Abstract classes may not be instantiated, and require subclasses to provide implementations for the abstract methods
-	Subclasses of an abstract class in Python are not required to implement abstract methods of the parent class
-	Python provides a module abc to help in defining and implementing Abstract Base Classes
-	A class that is derived from an abstract class which in turn inherits from ABC, cannot be instantiated unless all of its abstract methods which are decorated with `@abstractmethod` are overridden
-	Abstract methods which are decorated, declared in base class, where base class inherits from ABC can be used to force implementation in the child classes inheriting from base class


### Class method vs Static method
|Class Method	| Static Method|

|---------------|--------------|

|The class method takes `cls` (class) as first argument|	The static method does not take any specific parameter|
Class method can access and modify the class state|	Static Method cannot access or modify the class state|
The class method takes the class as parameter to know about the state of that class|	Static methods do not know about class state. These methods are used to do some utility tasks by taking some parameters|
`@classmethod` decorator is used here|	`@staticmethod` decorator is used here|


### Comprehensions
-	Comprehensions in Python provide us with a short and concise way to construct new sequences (such as lists, set, dictionary etc.) using sequences which have been already defined
-	Comprehensions cannot be used for Tuples
-	Python supports the following types of comprehensions:
    *	List Comprehensions
    *	Dictionary Comprehensions
    *	Set Comprehensions

### Dunder/Magic Methods
-	Dunder methods are a set of predefined methods you can use to enrich your classes
-	Dunder methods let you emulate the behavior of built-in types. For example, to get the length of a string you can call len('string'). But an empty class definition doesn’t support this behavior out of the box:

```

class NoLenSupport:
    pass

obj = NoLenSupport()
len(obj)
# TypeError: "object of type 'NoLenSupport' has no len()"
```

```
# To fix this, you can add a __len__ dunder method to your class:

class LenSupport:
    def __len__(self):
        return 42

obj = LenSupport()
print(len(obj)) # print out len as 42
```

### repr vs str
-	`str()` and `repr()` both are used to get a string representation of object
-	`str()` is used for creating output for end user while repr() is mainly used for debugging and development. 
-	`repr()` goal is to be unambiguous and str’s is to be readable
-	`repr()` compute the “official” string representation of an object (a representation that has all information about the abject) and str() is used to compute the “informal” string representation of an object (a representation that is useful for printing the object)

### Exception handling
-	A single try statement can have multiple except statements. This is useful when the try block contains statements that may throw different types of exceptions.
-	You can also provide a generic except clause, which handles any exception.
-	After the except clause(s), you can include an else-clause. The code in the else-block executes if the code in the try: block does not raise an exception.
-	The else-block is a good place for code that does not need the try: block's protection.

```
try:
    # You do your operations here

except Exception I:
    # If there is Exception I, then execute this block

except Exception II:
    # If there is Exception II, then execute this block

else:
    # If there is no exception then execute this block
```

### Sets
-	A set is an unordered collection of items. Every set element is unique (no duplicates) and must be immutable (cannot be changed).
-	However, a set itself is mutable. We can add or remove items from it.
-	Sets can also be used to perform mathematical set operations like union, intersection, symmetric difference, etc
