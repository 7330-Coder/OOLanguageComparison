# Chapter 5 : Classes (Python)

## Defining
The form of defining a class looks like:
```python
class ClassName:
  'class documentation'
  <statement-1>
  ...
  ...
  <statement-N>
```

## Creating new instances
Useing function notation to create new instances. The procedure to create an instance is similar to a function call.
```python
temp = ClassName()
```
This will create a new instance object named `temp` and we can access attributes of this objects (data or functions) using object name as a prefix.

## Constructing / Initializing
Class functions that begins with double underscore `__` are called special functions. One of the particular special functions is `__init__()` function, which is the constructor of a class. This function gets invoked whenever a new object of that class is initiated.

```python
class Vec2:
  def __init__(self, x, y): 
    self.x = x 
    self.y = y
  def getData(self):
  	return 'Vec2({self.x}, {self.y})'.format(self=self)

vector1 = Vec2(2, 3)
vector1.getData()		#output is Vec2(2, 3)
```

## Destructing / De-initializing
Similar to `__init__()` function, destructing function `__del__()` gets invoked whenever a current instance is about to be destroyed. 
```python
vector2 = Vec2(4, 5)
del vector2
vector2.getData()	# name 'vector2' is not defined
```
On the command del vector2, this binding is removed and the name vector2 is deleted from the corresponding namespace. However, the oject `Vec2(4, 5)` itself continues to exist in memory. If no other name is bound to it in the future, it is later automatically destroyed by garbage collection.

## Reference
- [_Programiz Python Tutorial_](https://www.programiz.com/python-programming/class)