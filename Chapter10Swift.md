# Chapter 10 : Reflection

### What reflection abilities are supported?
Reflection in Swift is easy using the struct Mirror, with it we can inspect the names and types of properties in an instance of a struct or an instance of a class.
### How is reflection used?

Imagine we have a struct called Book which looks like this:
```Swift
struct Book {
    let title: String
    let author: String?
    let published: Date
    let numberOfPages: Int
    let chapterCount: Int?
    let genres: [String]
}
```
Then we can create an instance of Book:
```Swift
let book = Book(title: "Harry Potter", author: "J.K. Rowling", published: Date(), numberOfPages: 450, chapterCount: 19, genres: ["Fantasy", "Best books ever"])
```
And then it is super easy to look at the properties if the Harry Potter book instance using the Mirror struct.
```Swift
let bookMirror = Mirror(reflecting: book)
for (name, value) in bookMirror.children {
    guard let name = name else { continue }
    print("\(name): \(type(of: value)) = '\(value)'")
}
// which prints:
// title: String = 'Harry Potter'
// author: Optional<String> = 'Optional("J.K. Rowling")'
// published: Date = '2016-10-02 19:17:43 +0000'
// numberOfPages: Int = '450'
// chapterCount: Optional<Int> = 'Optional(19)'
// genres: Array<String> = '["Fantasy", "Best books ever"]'
```
