# Chapter 3 : Types (Python)

## What types does the language support?
Python's built-in data types can be grouped as follows:

- Boolean
	- Values: True and False.
    - Mainly used in conditional expressions.

```python
flag = None
if condition1:
  flag = True
if flag:
  # do some stuff
```

- Numeric Types
	- int
    	- Integers.
        - Equivalent to C longs in Python 2.x.
        - Non-limited length in Python 3.x.
    - long
    	- Long Integers.
        - Non-limited length.
        - Only exists in Python 2.x.
    - float
    	- Floating-Point Numbers.
        - Equivalent to C doubles.
    - complex
    	- Complex Number.

```python
tempInt = -0x69
tempLong = 122L
tempFloat = 32.5e+18
tempComplex = 3.14+5J
tempStr = 'Hello World!'
tempList = ['Hello', 233, 'World', 70.5]
tempTuple = 'Hello', 233, 'World', 70.5)
```
    
- Sequences
	- str
    	- String.
        - Sequence of 8-bit characters in Python 2.x.
        - Sequence of Unicode characters in Python 3.x.
    - bytes
    	- Sequence of integers within a range of 0 to 255.
        - Only exists in Python 3.x.
    - byte array
    	- Similar to bytes but mutable.
    	- Only exists in Python 3.x.
    - list
    	- Array that contains varied type of elements.
        - Implements all of the common and mutable sequence operations.
	- tuple
    	- Similar to list but not mutable.
        - Implements all of the common sequence operations.

```python
tempStr = 'Hello World!'
tempList = ['Hello', 233, 'World', 70.5]
tempTuple = 'Hello', 233, 'World', 70.5)
tempBytes = bytes([6, 7, 60, 70, 0])
tempByteArray = bytearray([6, 7, 60, 70, 0])

tempByteArray[0] = 1   # Legal in Byte Array
tempBytes[0] = 1       # Illegal in Bytes		
tempList[2] = 1000     # Legal in List
tempTuple[2] = 1000    # Illegal in Tuple
```

- Sets
	- set
    	- Unordered collection of unique objects.
        - Available as built-in type since Python 2.6.
    - frozen set
    	- Similar to set but immutable.
        - Available as built-in type since Python 2.6.

```python
tempSet = Set(['Siyang', 'Yuhan', 'Fan'])
tempFrozenSet = Set(['Siyang', 'Yuhan', 'Fan'])

tempSet.add('Huanhuan')			# Legal in Set
tempFrozenSet.add('Huanhuan') 	# Illegal in Frozen Set
```


- Mappings
	- dict
    	- Python Dictionaries, hashmaps or associative arrays.
        - Elements of the list are associated with a definition.

```python
tempDict = {'name': 'Siyang','code':2333, 'gender': 'male'}
```
## Are both reference and value types supported?
In Python, a variable is just an identifier points to an object in memory. Therefore, variable does not have a type. The type belongs to the object. This is also the reason why variables in Python can be assigned to any type. Accroding to this feature, the concern is whether a type is mutable or not. From above, we know that `numeric`, `string`, `tuple` and `frozenset` are immutable. Names that are bound to an object of one of those immutable typs can only be rebound.

```python
def foo(arg):
  arg = 5
  print(arg)
x = 1
foo(x)    # output is 5
print(x)  # output is 1
```
In the code above, both x and arg points to the '1' in memory. In funciton foo, since `int` object is immutable, a new object with a value of '5' was created, and arg rebound to this object. While x still points to the object with value '1'.

```python
def foo(arg):
  arg.append(3)
x = [1, 2]
print(x)   # output is [1, 2]
foo(x)
print(x)   # output is [1, 2, 3]
```
In the code above, both x and arg points to the same list in memory. Since `list` object is mutable, function append allows arg having a new element at the end of the list. While x still points to the same list object, content of variable x also changed.

## Can new value types be created?
**Yes.** Creating a new value types by creating a class. For example, creating a new value type as 2-d vector.

```python
class Vec2:
  def __init__(self, x, y): 
    self.x = x 
    self.y = y
  def __sub__(self, other)
    dist = ((other[0] - self[0])**2 + (other[1] - self[1])**2)**0.5
    return dist
```

## Reference
- [_Programiz Python Tutorial_](https://www.programiz.com/python-programming/variables-datatypes)
- [_WikiBooks of Python_](https://en.wikibooks.org/wiki/Python_Programming/Data_Types#Built-in_Data_types)