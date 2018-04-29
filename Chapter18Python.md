# Chapter 18: Procedural programming
## Python

In Python, you can define a function outside of a class and then use it in the class body as a method.

```Python
    def func(self):
        print "func"

    class MyClass(object):
        myMethod = func
```
You can also add a function to a class after it has been defined:
```Python
    class MyClass(object):
        pass
    def func(self):
        print "func"
    MyClass.myMethod = func
```


