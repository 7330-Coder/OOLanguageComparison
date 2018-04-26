# Chapter 11: Memory management

## Python

### Overview
  Memory management in Python involves a private heap containing all Python objects and data structures. The management of this private heap is ensured internally by the Python memory manager. The Python memory manager has different components which deal with various dynamic storage management aspects, like sharing, segmentation, preallocation or caching.

### How will it work?
  At the lowest level, a raw memory allocator ensures that there is enough room in the private heap for storing all Python-related data by interacting with the memory manager of the operating system. On top of the raw memory allocator, several object-specific allocators operate on the same heap and implement distinct memory management policies adapted to the peculiarities of every object type. For example, integer objects are managed differently within the heap than strings, tuples or dictionaries because integers imply different storage requirements and speed/space tradeoffs. The Python memory manager thus delegates some of the work to the object-specific allocators, but ensures that the latter operate within the bounds of the private heap.

### Garbage Collection and Rference counting in Python
  **Garbage Collection**
Python’s memory allocation and deallocation method is automatic. The user does not have to preallocate or deallocate memory similar to using dynamic memory allocation in languages such as C or C++.
Python uses two strategies for memory allocation: Reference counting and Garbage collection. One can inspect the threshold for new objects (objects in Python known as generation 0 objects) by importing the gc module and asking for garbage collection thresholds:
  ```
  # loading gc
  import gc
 
  # get the current collection 
  # thresholds as a tuple
  print("Garbage collection thresholds:",
                     gc.get_threshold())
  ```

  **Rference counting**
Since Python makes heavy use of malloc() and free(), it needs a strategy to avoid memory leaks as well as the use of freed memory. The chosen method is called reference counting. The principle is simple: every object contains a counter, which is incremented when a reference to the object is stored somewhere, and which is decremented when a reference to it is deleted. When the counter reaches zero, the last reference to the object has been deleted and the object is freed.
An alternative strategy is called automatic garbage collection. (Sometimes, reference counting is also referred to as a garbage collection strategy, hence my use of ``automatic'' to distinguish the two.) The big advantage of automatic garbage collection is that the user doesn't need to call free() explicitly. (Another claimed advantage is an improvement in speed or memory usage -- this is no hard fact however.) The disadvantage is that for C, there is no truly portable automatic garbage collector, while reference counting can be implemented portably (as long as the functions malloc() and free() are available -- which the C Standard guarantees). Maybe some day a sufficiently portable automatic garbage collector will be available for C. Until then, we'll have to live with reference counts.


### References:
* [Greeks For Geeks]
* [Extending and Embedding the Python Interpreter]
* [Python/C API Reference Manual]


[Greeks For Geeks]: <https://www.geeksforgeeks.org/garbage-collection-python/>
[Extending and Embedding the Python Interpreter]: <https://docs.python.org/2.2/ext/about.html>
[Python/C API Reference Manual]: <https://docs.python.org/3/c-api/memory.html>