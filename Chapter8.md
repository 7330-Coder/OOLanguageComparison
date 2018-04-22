# Chapter 8 : Interfaces & Protocols

### What does the language support?
Swift support Protocols.

### What abilities does it have?
A protocol defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality. The protocol can then be adopted by a class, structure, or enumeration to provide an actual implementation of those requirements. Any type that satisfies the requirements of a protocol is said to conform to that protocol.

In addition to specifying requirements that conforming types must implement, you can extend a protocol to implement some of these requirements or to implement additional functionality that conforming types can take advantage of.
### How is it used?
Here's an example of a protocol with a single instance property requirement:
```
protocol FullyNamed {
    var fullName: String { get }
}
```
The FullyNamed protocol requires a conforming type to provide a fully-qualified name. The protocol doesn’t specify anything else about the nature of the conforming type—it only specifies that the type must be able to provide a full name for itself. The protocol states that any FullyNamed type must have a gettable instance property called fullName, which is of type String.

Here’s an example of a simple structure that adopts and conforms to the FullyNamed protocol:
```
struct Person: FullyNamed {
    var fullName: String
}
let john = Person(fullName: "John Appleseed")
// john.fullName is "John Appleseed"
```