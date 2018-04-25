# Functional Programming
   1. Concepts
   - Swift supports a lot of programming paradigms like functional programming, procedural programming and etc.
   - For the functional programming in Swift, it is achieved by passing a function / closure as an parameter to the method to be execute, and tells the method what should be done in the function / closure.
   2. Code examples
   - Use functional programming to sort an array of numbers by passing a function
   ```Swift
   func smaller(_ num1: Int, _ num2: Int) -> Bool {
       return num1 < num2
   }
   func greater(_ num1: Int, _ num2: Int) -> Bool {
       return num1 > num2
   }
   let numbers = [1, 5, 6, 2, 6, 2, 8]
   let ascendingOrderNumbers = numbers.sorted(by: smaller)
   let decendingOrderNunbers = numbers.sorted(by: greater)
   print("Ascending Order: \(ascendingOrderNumbers)")
   print("Decending Order: \(decendingOrderNunbers)")
   ```
   - Ouput
   ```
   Ascending Order: [1, 2, 2, 5, 6, 6, 8]
   Decending Order: [8, 6, 6, 5, 2, 2, 1]
   ```
   - Use functional programming to sort an array of numbers by passing a closure
   ```Swift
   let numbers = [1, 5, 6, 2, 6, 2, 8]
   let numbers = [1, 5, 6, 2, 6, 2, 8]
   let ascendingOrderNumbers = numbers.sorted {
       return $0 < $1
   }
   let decendingOrderNunbers = numbers.sorted {
       return $0 > $1
   }
   print("Ascending Order: \(ascendingOrderNumbers)")
   print("Decending Order: \(decendingOrderNunbers)")
   ```
   - Ouput
   ```
   Ascending Order: [1, 2, 2, 5, 6, 6, 8]
   Decending Order: [8, 6, 6, 5, 2, 2, 1]
   ```