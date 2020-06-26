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
-	We can use super() to invoke constructor and method of parent class
-	We can use in built issubclass() method to verify whether a particular class is a subclass of another class. Built-in function is issubclass(paramOne, paramTwo) where paramOne and paramTwo can be either class names or class's object name
-	It is recommended to call the parent class constructor from the child class

### Abstraction
-	Abstraction means hiding the complexity and only showing the essential features of the object. So in a way, Abstraction means hiding the real implementation
-	Abstraction in Python is achieved by using abstract classes and interfaces
