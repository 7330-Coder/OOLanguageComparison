# Chapter 4 : Types



### What types does the language support?
Swift provides its own versions of all fundamental C and Objective-C types, including Int for integers, Double and Float for floating-point values, Bool for Boolean values, and String for textual data. Swift also provides powerful versions of the three primary collection types, Array, Set, and Dictionary, as described in Collection Types. In addition to familiar types, Swift introduces advanced types such as tuples and optional types.

### Are both reference and value types supported?
Types in Swift fall into one of two categories: first, “value types”, where each instance keeps a unique copy of its data, usually defined as a struct, enum, or tuple. The second, “reference types”, where instances share a single copy of the data, and the type is usually defined as a class. In this post we explore the merits of value and reference types, and how to choose between them.

### Can new value types be created?
There are many cases when we need to create our own data type. Suppose we want to create a Type that represents Student, we can create it using a class as:
```Swift
class Student {

}
```
Now a group of students can be represented as an array as:
```
var students:Array<Student> = []
```
The above declaration can be made more readable by creating your own type for Array<Student> using typealias as:
```
typealias Students = Array<Student>
```
Now we can make our code more readable as:
```
var students:Students = []
```