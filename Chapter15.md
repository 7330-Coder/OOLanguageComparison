# Closures
1. Definition
    - Closures are self-contained blocks of functionality that can be passed around and used in your code.
    - The syntax is as the following
    ```Swift
    { (parameters) -> return type in
        statements
    }
    ```
    - The parameters can be omitted to use $0, $1... and so on, the same sequence as they appear in the parameters.
2. Example
    - Using closures to do math operation
    ```Swift
    var addClosure: (Int, Int) -> Int

    addClosure = { (num1, num2) in
        return num1 + num2
    }
    
    func doOperation(forNum num1: Int, andNum num2: Int, withClosure closure: (Int, Int) -> Int) -> Int {
        return closure(num1, num2)
    }
    
    let num1 = 1
    let num2 = 2
    let result = doOperation(forNum: num1, andNum: num2, withClosure: addClosure)
    
    print(result)
    ```
    Output:
    ```
    3
    ```
    - Easier way to write is as following:
    ```Swift
    let num1 = 1
    let num2 = 2
    let result = doOperation(forNum: num1, andNum: num2) { (num1, num2) in
        return num1 + num2
    }
    print(result)
    ```
    Output:
    ```
    3
    ```
    - Easiest way write it is as following:
    ```Swift
    let num1 = 1
    let num2 = 2
    let result = doOperation(forNum: num1, andNum: num2) {
        return $0 + $1
    }
    print(result)
    ```
    Output:
    ```
    3
    ```
    