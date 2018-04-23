# Chapter 12 : Comparisons of references and values

 ### How are values compared? (i.e. comparing two strings)

Value equality is checked using the == operator, which returns whether or not two instances are equivalent to each other.

Reference equality is checked using the === operator, which returns whether or not two references refer to the same object. Reference equality is only meaningful when reference types are being compared, whereas value equality pertains to both reference and value types.
```Swift
let password = "HelloWorld"
let repeatPassword = "HelloWorld"
if ((password.elementsEqual(repeatPassword)) == true)
{
   print("Passwords are equal")
} else {
   print("Passwords are not equal")
}
```
Case insensitive comparison of two Strings in Swift:
```Swift
let valueExpected = "SUCCESS"
let valueProvided = "success"
if valueExpected.caseInsensitiveCompare(valueProvided) == ComparisonResult.orderedSame
{
    print("Strings are equal")
}
```