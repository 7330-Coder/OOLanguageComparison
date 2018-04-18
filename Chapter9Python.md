# Chapter 9 : Inheritance & Extension (Python)
Inheritance means defining a new class with little modification to an existing class. The new class is called **derived (or child) class** and the one from which the new class inherits is called the **base (or parent) class**. Derived class inherits features from the base class and adding new features to it. In Python, The inheritance syntax is shown below:
```python
class ParentClass:
  Body of Parent Class
  ...
class ChildClass(ParentClass):
  Body of Child Class
  ...
```
To check if a class is a child class of another, use `issubclass()`. For example, the retuen value of `issubclass(bool, int)` is `True`, since bool is a subclass of int.
To check is an instance's type, use `isinstance()`. For example, the retuen value of `isinstance(obj, int)` is `True` when `obj.__class__` is int or other class derived from int.

Python support multiple inheritance, which the features of all parent classes are inherited into the child class. The multiple inheritance syntax is shown below:
```python
class ParentClass1:
  Body of Parent Class1
  ...
class ParentClass2:
  Body of Parent Class2
  ...
class ChildClass(ParentClass1, ParentClass2):
  Body of Child Class
  ...
```

Python also support multilevel inheritance, which a child class can inherit from another child class. The features of the "grandparent" class and the parent class are inherited into the new child class. The multilevel inheritance syntax is shown below:
```python
class ParentClass:
  Body of Parent Class
  ...
class ChildClass1(ParentClass):
  Body of Child Class1
  ...
class ChildClass2(ChildClass1):
  Body of Child Class2
  ...
```

In multiple inheritance scenario, any specified attribute is searched first in the current class. If not found, the search continues into parent classes in depth-fist, left-right fashion. In the code example about `ChildClass2` above, the search order is [`ChildClass2`, `ChildClass1`, `ParentClass`, `object`]. This set of rules used to find the linear order is called **Method Resolution Order(MRO)**.

MRO ensures that a class always appears before its parents, thus prevent local precedence ordering and provide monotonicity.



## Reference
- [_Programiz Python Tutorial_](https://www.programiz.com/python-programming/multiple-inheritance)