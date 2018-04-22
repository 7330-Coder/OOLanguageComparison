# Chapter 7 : Properties

### Getters and Setters (write your own or built in?)
In Swift, like other languages, getters and setters don't need to be declared for public variables. The getter and setter implementation can be overwritten in Swift for all types of variables, including private.
```
//within a class or structure

var variableName: dataType {
    get {
        //code to execute
        return someValue
    }
    set(newValue) {
        //code to execute
    }
}
```
Usually used to set getter and setter behavior for classes within classes, and private variables.
### Backing Variables and Computed Properties
A Swift property does not have a corresponding instance variable, and the backing store for a property is not accessed directly. This approach avoids confusion about how the value is accessed in different contexts and simplifies the property's declaration into a single, definitive statement. All information about the property, including its name, type, and memory management characteristics, is defined in a single location as part of the type's definition.
```
struct Point {
    var x = 0.0, y = 0.0
}
struct Size {
    var width = 0.0, height = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
    }
}
var square = Rect(origin: Point(x: 0.0, y: 0.0),
                  size: Size(width: 10.0, height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0, y: 15.0)
print("square.origin is now at (\(square.origin.x), \(square.origin.y))")
```