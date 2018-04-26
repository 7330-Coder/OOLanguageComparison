# Chapter 13: Null/nil references
## Python
### Python's null Equivalent: None
The equivalent of the null keyword in Python is None. It was designed this way for two reasons:
* Many would argue that the word "null" is somewhat esoteric. It's not exactly the most friendliest word to programming novices. Also, "None" refers exactly to the intended functionality - it is nothing, and has no behaviour.
* In most object-oriented languages, the naming of objects tend to use camel-case syntax. eg. ThisIsMyObject. As you'll see soon, Python's None type is an object, and behaves as one.

The syntax to assign the None type to a variable, is very simple. As follows:
```my_none_variable = None```
### Why Use Python's None Type?
There are many cases on why you would use None.
Often you will want to perform an action that may or may not work. Using None is one way you can check the state of the action later. 
Another scenario would be where you may need to instantiate a class, depending on a condition. You could assign a variable to None, then optionally later assign it to an object instance. Then after that you may need to check if the class has been instantiated. There are countless examples - feel free to provide some in the comments!

### Does the language have features for handling null/nil references?
The Null object is returned by functions that don’t explicitly return a value. It supports no special operations. There is exactly one null object, named None (a built-in name). type(None)() produces the same singleton. It is written as None.

