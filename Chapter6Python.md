# Chapter 6 : Instance Reference Name in Data Type

## this or self?
It can be said that both `self` and `this` are used for accessing the variables and functions associated with the current instance. The difference in Python is to include `self` explicitly as the first parameter to an instance method in Python. Whereas `this` is not used like this in other OO language like JAVA or C#.  Actually, `self` is not a keyword in Python, it can by anything but using `self` now becomes a convention.
Suppose we have a Vec2 class defined as follows:
```python
class Vec2:
  def __init__(self, x, y): 
    self.x = x 
    self.y = y
  def getData(self):
  	return 'Vec2({self.x}, {self.y})'.format(self=self)

vector1 = Vec2(2, 3)
```
A function call like:
```python
vector1.getData()
```
can be internally transform to
```python
Vec2.getData(vector1)
```
Python could do something like requiring declarations likw JAVA or C#, to distinguish normal names from atributes. But Python holds the principle of **Explicit is better than implicit** and that is the reason why `self` is needed.