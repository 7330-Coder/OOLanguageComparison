# Chapter 3 : Name spaces (Python)


## How are name spaces implemented?
Everthing in Python is an object and **Name** is an identifier given to objects.
A **namespace** is a mapping of every defined names to its corresponding objects. Most namespaces are currently implemented as Python dictionaries, in which names are keys and objects are values. 

## How are name spaces used?
Namespaces are created at different moments with varied lifetimes. In Python, namespaces can be:
- The set of built-in names (containing built-in names such as abs());
	Created when Python interpreter starts up.
	Deleted when the interpreter quits.
- The global names in a module;
	Created when the module definition is read in.
	Deleted when the interpreter quits.
- The local names in a function invocation.
	Created when the function is invoked.
	Deleted when the function returns or raises unhandled exception within the function.