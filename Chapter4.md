# Chapter 3 : Types (Python)

## What types does the language support?
Python's built-in data types can be grouped as follows:

- Boolean
	- Values: True and False.
    - Mainly used in conditional expressions.

```
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

```
tempInt = -0x69
tempLong = 0122L
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

```
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

```
tempSet = Set(['Siyang', 'Yuhan', 'Fan'])
tempFrozenSet = Set(['Siyang', 'Yuhan', 'Fan'])

tempSet.add('Huanhuan')			# Legal in Set
tempFrozenSet.add('Huanhuan') 	# Illegal in Frozen Set
```


- Mappings
	- dict
    	- Python Dictionaries, hashmaps or associative arrays.
        - Elements of the list are associated with a definition.

```
tempDict = {'name': 'Siyang','code':2333, 'gender': 'male'}
```
## Are both reference and value types supported?


## Can new value types be created?
**Yes.**

## Reference
- [_Programiz Python Tutorial_](https://www.programiz.com/python-programming/variables-datatypes)
- [_WikiBooks of Python_](https://en.wikibooks.org/wiki/Python_Programming/Data_Types#Built-in_Data_types)