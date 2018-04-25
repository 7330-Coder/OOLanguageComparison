# Chapter 19 : Functional programming

## Does the language support functional programming?
Yes. **Functional programming** decomposes a problem into a set of functions. Each functio only operates on its inputs and produce outputs. Functions that have no side effects at all are called **purely functional**. Avoiding side effects means not using data structures that get updated as a program runs; every function’s output must only depend on its input. 

### Iterators
Start by looking at an important foundation for writing functional-style programs in Python: **iterators**. An iterator is an object representing a stream of data; this object returns the data one element at a time. A method called `__next__()` that takes no arguments and always returns the next element of the stream. The built-in `iter()` function takes an arbitrary object and tries to return an iterator that will return the object’s contents or elements. 
Python expects iterable objects in several different contexts, the most important being the for statement.
```python
for i in iter(obj):
    print(i)
```
Two common operations on an iterator’s output are 1) performing some operation for every element, 2) selecting a subset of elements that meet some condition. List comprehensions and generator expressions are a concise notation for such operations.
```python
stripped_list = [line.strip() for line in line_list if line != ""]
```

### Generators
Generators are a special class of functions that simplify the task of writing iterators. Regular functions compute a value and return it, but generators return an iterator that returns a stream of values.
```python
# A recursive generator that generates Tree leaves in in-order.
def inorder(t):
    if t:
        for x in inorder(t.left):
            yield x

        yield t.label

        for x in inorder(t.right):
            yield x
```
On executing the `yield` expression, the generator outputs the value, similar to a return statement. The big difference between `yield` and `return` is that on reaching a `yield` the generator’s state of execution is suspended and local variables are preserved. On the next call to the generator’s `__next__()` method, the function will resume executing.