# Chapter 14: Errors and exception handling
## Python
### Exception handling
Here is a list of some standard exceptions in Python:

  EXCEPTION NAME | DESCRIPTION
  --- | ---
  Exception	 | Base class for all exceptions
  StopIteration	 | Raised when the next() method of an iterator does not point to any object.
  SystemExit	 | Raised by the sys.exit() function.  
  StandardError	 | Base class for all built-in exceptions except StopIteration and SystemExit.
  ArithmeticError	 | Base class for all errors that occur for numeric calculation.
  OverflowError	 | Raised when a calculation exceeds maximum limit for a numeric type.
  FloatingPointError   | Raised when a floating point calculation fails.
  ZeroDivisionError	 | Raised when division or modulo by zero takes place for all numeric types.
  AssertionError	 | Raised in case of failure of the Assert statement.
  AttributeError	 | Raised in case of failure of attribute reference or assignment.
  EOFError	 | Raised when there is no input from either the raw_input() or input() function and the end of file is reached.
  ImportError	 | Raised when an import statement fails.
  KeyboardInterrupt	 | Raised when the user interrupts program execution, usually by pressing Ctrl+c.
  LookupError	 | Base class for all lookup errors.
  IndexError   |  Raised when an index is not found in a sequence.
  IOError    | Raised when an input/ output operation fails, such as the print statement or the open() function when trying to open a file that does not exist.
  SystemError	  | Raised when the interpreter finds an internal problem, but when this error is encountered the Python interpreter does not exit.
  SystemExit	  | Raised when Python interpreter is quit by using the sys.exit() function. If not handled in the code, causes the interpreter to exit.
  TypeError	  | Raised when an operation or function is attempted that is invalid for the specified data type.
  ValueError	  | Raised when the built-in function for a data type has the valid type of arguments, but the arguments have invalid values specified.
  RuntimeError	  | Raised when a generated error does not fall into any category.
  NotImplementedError	  | Raised when an abstract method that needs to be implemented in an inherited class is
  
  There are (at least) two distinguishable kinds of errors: syntax errors and exceptions.
Syntax errors, also known as parsing errors:
```
>>> while True print('Hello world')
File "<stdin>", line 1
while True print('Hello world')
             ^
SyntaxError: invalid syntax
```
It is possible to write programs that handle selected exceptions. Look at the following example, which asks the user for input until a valid integer has been entered, but allows the user to interrupt the program; note that a user-generated interruption is signalled by raising the KeyboardInterrupt exception.
```
while True:
    try:
      x = int(input("Please enter a number: "))
      break
    except ValueError:
      print("Oops!  That was no valid number.  Try again...")
```

  The try statement works as follows.
  * First, the try clause (the statement(s) between the try and except keywords) is executed.
  * If no exception occurs, the except clause is skipped and execution of the try statement is finished.
  * If an exception occurs during execution of the try clause, the rest of the clause is skipped. Then if its type matches the exception named after the except keyword, the except clause is executed, and then execution continues after the try statement.
  * If an exception occurs which does not match the exception named in the except clause, it is passed on to outer try statements; if no handler is found, it is an unhandled exception and execution stops with a message as shown above.

  A try statement may have more than one except clause, to specify handlers for different exceptions. At most one handler will be executed. Handlers only handle exceptions that occur in the corresponding try clause, not in other handlers of the same try statement. An except clause may name multiple exceptions as a parenthesized tuple, for example:

  ```Python
  except (RuntimeError, TypeError, NameError):
     pass
  ```


  #### Raising Exception

  The raise statement allows the programmer to force a specified exception to occur. The sole argument to raise indicates the exception to be raised. This must be either an exception instance or an exception class (a class that derives from Exception). If an exception class is passed, it will be implicitly instantiated by calling its constructor with no arguments. The general syntax for the raise statement is as follows.

  ```Python
    raise [Exception [, args [, traceback]]]
  ```

  Exception is the type of exception (for example, NameError) and argument is a value for the exception argument. The argument is optional; if not supplied, the exception argument is None.The final argument, traceback, is also optional (and rarely used in practice), and if present, is the traceback object used for the exception.
  If you need to determine whether an exception was raised but don’t intend to handle it, a simpler form of the raise statement allows you to re-raise the exception:

  ```Python
>>> try:
        raise NameError('HiThere')
    except NameError:
        print('An exception flew by!')
    raise
An exception flew by!
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
NameError: HiThere
  ```

  Python also allows you to create your own exceptions by deriving classes from the standard built-in exceptions, which is similar to Java -- Writing your own exceptions and then throwing the exceptions.

  This is an example related to RuntimeError. One class is created that is subclassed from RuntimeError. This is useful when you need to display more specific information when an exception is caught.

  In the try block, the user-defined exception is raised and caught in the except block. The variable e is used to create an instance of the class Networkerror.

  ```Python
    class Networkerror(RuntimeError):
       def __init__(self, arg):
          self.args = arg
    So once you defined above class, you can raise the exception as follows −

    try:
       raise Networkerror("Bad hostname")
    except Networkerror,e:
       print e.args
  ```
   #### Predefined Clean-up Actions
  When we are trying to open a file and print its contents to the screen by using the following code.

  ```Python
  for line in open("myfile.txt"):
    print(line, end="")
  ```

  The problem with this code is that it leaves the file open for an indeterminate amount of time after this part of the code has finished executing. This is not an issue in simple scripts, but can be a problem for larger applications. The with statement allows objects like files to be used in a way that ensures they are always cleaned up promptly and correctly.

  ```Python
  with open("myfile.txt") as f:
    for line in f:
        print(line, end="")
  ```

  It is much convenient to use the _with_ statement when opening a file, however, in Java, you still need to use _try-catch_ statement to catch the exceptions could happened during opening files.


  
