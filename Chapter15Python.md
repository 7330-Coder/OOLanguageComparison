# Chapter15 Lambda Expressions, Closures, or Functions as Types
## Python

### Lambda Operator

The lambda operator or lambda function is a way to create small anonymous functions, i.e. functions without a name. These functions are throw-away functions, i.e. they are just needed where they have been created. Lambda functions are mainly used in combination with the functions filter(), map() and reduce(). The lambda feature was added to Python due to the demand from Lisp programmers. 
The general syntax of a lambda function is quite simple:
```python
lambda argument_list: expression 
```
The argument list consists of a comma separated list of arguments and the expression is an arithmetic expression using these arguments. You can assign the function to a variable to give it a name. 
The following example of a lambda function returns the sum of its two arguments:
```python
>>> f = lambda x, y : x + y
>>> f(1,1)
2
```

### Python Closures
A Closure is a function object that remembers values in enclosing scopes even if they are not present in memory.

* It is a record that stores a function together with an environment: a mapping associating each free variable of the function (variables that are used locally, but defined in an enclosing scope) with the value or reference to which the name was bound when the closure was created.
* A closure—unlike a plain function—allows the function to access those captured variables through the closure’s copies of their values or references, even when the function is invoked outside their scope.
```python
# Python program to illustrate
# closures
def outerFunction(text):
    text = text
 
    def innerFunction():
        print(text)
 
    return innerFunction # Note we are returning function WITHOUT parenthesis
 
if __name__ == '__main__':
    myFunction = outerFunction('Hey!')
    myFunction()
```
Output:
```python
omkarpathak@omkarpathak-Inspiron-3542:
~/Documents/Python-Programs/$ python Closures.py 
Hey!
```
1. As observed from above code, closures help to invoke function outside their scope.
2. The function innerFunction has its scope only inside the outerFunction. But with the use of closures we can easily extend its scope to invoke a function outside its scope.
###### When and why to use Closures:
A Closure is a function object that remembers values in enclosing scopes even if they are not present in memory.

* It is a record that stores a function together with an environment: a mapping associating each free variable of the function (variables that are used locally, but defined in an enclosing scope) with the value or reference to which the name was bound when the closure was created.
* A closure—unlike a plain function—allows the function to access those captured variables through the closure’s copies of their values or references, even when the function is invoked outside their scope.


### functions as types
A first-class function is not a particular kind of function. All functions in Python are first-class functions. To say that functions are first-class in a certain programming language means that they can be passed around and manipulated similarly to how you would pass around and manipulate other kinds of objects (like integers or strings). You can assign a function to a variable, pass it as an argument to another function, etc. The distinction is not that individual functions can be first class or not, but that entire languages may treat functions as first-class objects, or may not.






























