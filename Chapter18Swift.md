# Procedural Programming
- Swift itself supports procedural programming, but not so many people do this in the App development supported by Swift like iOS and macOS.
- To do procedural programming is Swift, just write some functions outsize the class. And then you can call them in another function, and you can also call them within the class.
- Code example1
  ```Swift
  func add(_ num1: Int, _ num2: Int) -> Int {
      return num1 + num2
  }
  print(add(1, 2))
  ```
  Output:
  ```
  3
  ```
- Code example2
  ```Swift
  func sumTo(_ num: Int) -> Int {
      if (num == 1) {
          return 1;
      }
      else {
          return num + sumTo(num - 1)
      }
  }
  print(sumTo(100))
  ```
  Output:
  ```
  5050
  ```