# Chapter 7 : Properties (Python)

## Getters and Setters (write your own or built in?)
In Python, there are no built-in getters and setters. The code block below is to define getter and setter interface.
```Python
class Egg:
  def __init__(self, price = 0): 
    self.set_price(price)

  def compute_tax(self)
    return get_price(self) * 0.04

  def set_price(self, value):
    if value < 0
  	  raise ValueError("Price below 0 is not possible")
  	self._price = value

  def get_price(self):
  	return self._price

tempEgg = Egg(5)
print(tempEgg.compute_tax())	# output is 0.2
```

## Backing Variables and Computed Properties
But the method above is not a great method since it would reduce the reusabilty. Coders should modify the code from directly get `tempEgg.price` to `tempEgg.get_price()` and similar to setter cases. In Python, it is a convention to use `@property` to implement getters and setters. The sample code are as follows:
```python
class Egg:
  def __init__(self, price = 0)
    self._price = price
  
  def compute_tax(self)
    return self._price * 0.04

  @property
  def get_price(self)
    return self._price;

  @price.setter
  def set_price(self, value)
    if value < 0
  	  raise ValueError("Price below 0 is not possible")
  	self._price = value

tempEgg = Egg(5)
print(tempEgg.compute_tax())	# output is 0.2
```
From the code above, it is clearer to see using `@property` allows coders to write simpler code when backing variables and computed properties.

Actually, `property()` is a built-in function that creates and returns a property object. The signiture of this function is:
```python
property(fget=None, fset=None, fdel=None, doc=None)
```
where, `fget` is function to get value of the attribute, `fset` is function to set value of the attribute, `fdel` is function to delete the attribute and `doc` is a string (like a comment). 
A property object has three methods, `getter()`, `setter()` and `delete()` to specify `fget`, `fset` and `fdel`.This means,
```python
price = property(get_price, set_price)
```
is equivalant to
```python
price = property()
price = price.getter(get_price)
price = price.setter(get_price)
```
In conclusion, depending on the way we access a property object, it dispatches to perform either "getters", "setters" or "delete". The dispatch functions are specified when the property object is created using decorators.