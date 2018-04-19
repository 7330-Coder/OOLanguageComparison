# Chapter 10 : Reflection (Python)

## What reflection abilities are supported?

Python have the ability to find out the type, class, attributes and methods of an object at runtime. This referred to as **reflection**. It offers programmers great flexibility since the program is able to examine and modify its own structure and behavior at runtime. For example, dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object to invoke its method. In Python, reflection-enabling functions include `type()`, `isinstance()`, `callable()`, `dir()` and `getattr()`.

## How is reflection used?

### Set Attributes of an Object
The `setattr()` method sets the value of given attribute of an object and do not have return value.
If the attribute is not found, `setattr()` creates a new attribute using the given name and value. But it is only possible when the object implements __dict__() method.
```python
class person:
  name = ""
  def __init__(self, name):
    self.name = name
p = person()
```
If the attribute name is known and can be hard-coded:
```python
p.age = 32
```
If the attribute name and value will be determined at runtime:
```python
setattr(p, name, value)
```

### Get Attributes of an Object
The `getattr()` method returns the value of the named attribute of an object. It also allows the coder to specify a default value to be returned, when the object does not have an attribute of the given name
```python
class person:
  name = "Siyang"
  age = 32

p = person()
print('The gender is:', getattr(p, 'gender, 'Male'))	# Output: The gender is: Male
print('The gender is:', getattr(p, 'gender))			    # AttributeError: 'person' object has no attribute 'gender'
```
If the attribute name and default value will be determined at runtime:
```python
getattr(p, name, default_value)
```

### Find Out Type of an Object
If a single object is passed to `type()` built-in, it returns type of the given object. If three arguments (name, bases and dict) are passed, it returns a new type object. 
```python
print(type(3).__name__ == "int")		    # Output is True
print(type('Hello').__name__ == "str")	# Output is True
```
If the object will be determined at runtime:
```python
type(object)
type(name, bases, dict)
```

### Determines Whether an Object is an instance or Not
The `isinstance()` function checks if the object (first argument) is an instance or subclass of classinfo class (second argument).
```python
class person:
  name = "Siyang"

p = person()
print(isinstance(p, person))	# Output is True
```
If the object and class name will be determined at runtime:
```python
print(isinstance(object, class_name))
```

### Determine Whether a Class is a Subclass of Another Class
The `isinstance()` function checks if the object argument (first argument) is a subclass of classinfo class (second argument).
```Python
class Plant: 
  pass
class Tree(Plant):
  pass

tree = Tree()
print(issubclass(Tree, Plant))           # Output is True
print(issubclass(Tree, (list, Tree)))	   # Output is True
```
Note that class is considered a subclass of itself.

### Determines whether an Object Can be Called or Not
The `callable()` method returns True if the object passed appears callable. If not, it returns False.
```python
print(callable(2))	# Output is False
```
The code block below shows the class `person` and the instance of this class appears to be callable, and are callable in this case.
```python
class person:
  name = "Siyang"
  def __call__(self):
    print(self.name)

p = person()
print(callable(person))		# Output is True
print(callable(p))			  # Output is True
```
The code block below shows the class `person` is callable.
```Python
class person:
  name = "Siyang"
  def printName(self):
    print(self.name)

print(callable(person))		# Output is True
```
However the code block below will raise an error since the instance of 'person' class is not callable
```python
p = person()
p()				# Error: 'Foo' object is not callable
```
In conclusion, if `callable()` returns True, call to the object may still fail. If `callable()` returns False, call to the object will certainly fail.

## Reference
- [_Programiz Python Tutorial_](https://www.programiz.com/python-programming/methods/built-in/)
- [_Python Developer's Guide_](https://www.python.org/dev/peps/pep-0363/)