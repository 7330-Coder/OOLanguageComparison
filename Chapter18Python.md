# Chapter 18: Procedural programming
## Python
There are four main Python coding styles: imperative, functional, object-oriented, and procedural. (Some people combine imperative and functional coding styles. I choose not to combine them here because I view them as completely separate styles.) You may or may not agree that all four forms are valid or even useful—but nevertheless Python makes them all available. Let’s take a look at the pros and cons of each approach as well as some examples of usage.
#### Comparing the four Python coding styles
1. Functional: Every statement is treated as a mathematical equation and any form of state or mutable data are avoided. The main advantage of this approach is that there aren’t any side effects to consider. In addition, this coding style lends itself well to parallel processing because there is no state to consider. Many developers prefer this coding style for recursion and for lambda calculus.
2. Imperative: Computation is performed as a direct change to program state. This style is especially useful when manipulating data structures and produces elegant, but simple, code.
3. Object-oriented: Relies on data fields that are treated as objects and manipulated only through prescribed methods. Python doesn’t fully support this coding form because it can’t implement features such as data hiding. However, this remains a useful coding style for complex applications because it supports encapsulation and polymorphism. This coding style also favors code reuse.
4. Procedural: Tasks are treated as step-by-step iterations where common tasks are placed in functions that are called as needed. This coding style favors iteration, sequencing, selection, and modularization.

The examples used here all answer a common question so that you can more easily compare the coding styles. Normally, you’d use a particular coding style to meet a specific need, but showing four different examples wouldn’t be as helpful because you really need to see the same example presented four different ways to form an opinion on each style. So all these examples answer the same need, computing the sum of the following list:
```python
MyList = [1, 2, 3, 4, 5]
```
##### 1. Using the functional coding style
The functional coding style treats everything like a math equation. There are a number of ways to compute the sum of MyList using a functional style. However, the two most common would be to use a local function or a lambda expression—note that they don’t necessarily have to conform to Pep-8 in order to work. Here is the local function approach in Python 3.4:

```python
import functools
MyList = [1, 2, 3, 4, 5]
def AddIt(X, Y):
    return (X + Y)
Sum = functools.reduce(AddIt, MyList)
print(Sum)
```
The lambda expression approach is simpler (or, at least, shorter):
```python
import functools
MyList = [1, 2, 3, 4, 5]
Sum = functools.reduce(lambda x, y: x + y, MyList)
print(Sum)
```
##### 2. Using the imperative coding style
The focus of imperative programming is on how a program operates. It changes state information as needed in order to achieve a goal. Here is an example of how the imperative coding style might look for adding the elements of MyList:
```python
MyList = [1, 2, 3, 4, 5]
Sum = 0
for X in MyList:
    Sum += X
print(Sum)
```
Notice how this sample differs from the previous samples. The value of Sum changes with each iteration of the loop. As a result, Sum has state.
##### 3.Using the object-oriented coding style
The object-oriented coding style is all about increasing the ability of applications to reuse code and making code easier to understand. The encapsulation that object-orientation provides allows developers to treat code as a black box. Using object-orientation features like inheritance makes it easier to expand the functionality of existing code. Here is the MyList example in object-oriented form:

```python
class ChangeList:
    def __init__(self, MyList):
        if type(MyList) is list:
            self.MyList = MyList
        else:
            self.MyList =[]
    def DoAdd(self):
        self.Sum = sum(self.MyList)
CreateSum = ChangeList([1, 2, 3, 4, 5])
CreateSum.DoAdd()
print(CreateSum.Sum)
```
In this case, CreateSum is an instance of ChangeList. The inner workings of ChangeList don’t matter to the person using it. All that really matters is that you can create an instance using a list and then call the DoAdd() method to output the sum of the list elements. Because the inner workings are hidden, the overall application can be easier to understand.


#### 4. Using the procedural coding style

The procedural style relies on procedure calls to create modularized code. It seeks to simplify the application code by creating small pieces that a developer can view easily. Even though the procedural coding style is an older form of application development, it’s still a viable approach when a task lends itself to step-by-step execution. Here’s an example of the procedural coding style:
```python
def DoAdd(MyList):
    Sum = 0
    if type(MyList) is list:
        for X in MyList:
            Sum += X
    return Sum
MyList = [1, 2, 3, 4, 5]
print(DoAdd(MyList))
```
Notice how the use of a function, DoAdd(), simplifies the overall code in this case. The execution is still systematic, but the code is easier to understand because it’s broken into chunks.

 You can find more information about the functional and procedural programming from [article](https://blog.newrelic.com/2015/04/01/python-programming-styles/).









