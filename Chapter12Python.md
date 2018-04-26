# Chapter 12: Comparisons of references and values

## Python

**Assume variable a holds 10 and variable b holds 20, then** 
   ``` #!/usr/bin/python
    a = 21
    b = 10
    c = 0
        
    if ( a == b ):
       print "Line 1 - a is equal to b"
    else:
       print "Line 1 - a is not equal to b"
    
    if ( a != b ):
       print "Line 2 - a is not equal to b"
    else:
       print "Line 2 - a is equal to b"
        
    if ( a <> b ):
       print "Line 3 - a is not equal to b"
    else:
       print "Line 3 - a is equal to b"
        
    if ( a < b ):
       print "Line 4 - a is less than b" 
    else:
       print "Line 4 - a is not less than b"
        
    if ( a > b ):
       print "Line 5 - a is greater than b"
    else:
       print "Line 5 - a is not greater than b"
        
    a = 5;
    b = 20;
    if ( a <= b ):
       print "Line 6 - a is either less than or equal to  b"
    else:
       print "Line 6 - a is neither less than nor equal to  b"
        
    if ( b >= a ):
       print "Line 7 - b is either greater than  or equal to b"
    else:
       print "Line 7 - b is neither greater than  nor equal to b"
```
           

**When you execute the above program it produces the following result -**
  ```
    Line 1 - a is not equal to b
    Line 2 - a is not equal to b
    Line 3 - a is not equal to b
    Line 4 - a is not less than b
    Line 5 - a is greater than b
    Line 6 - a is either less than or equal to b
    Line 7 - b is either greater than or equal to b
  ```
  
  