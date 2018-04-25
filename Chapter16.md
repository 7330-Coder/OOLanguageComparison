# Listeners and Event Handlers
1. Listeners
    - Using listeners in Swift is to add willSet and didSet for the property. Putting them in a bracket after the property definition. willSet will be called automatically before the new value is set, and didSet will be called automatically after the new value is set. In willSet, developer can get the new value of the property through newValue variable. And in didSet, developer can get the old value of the property through the oldValue variable
    - Code Example
    ```Swift
    var number = 0 {
        didSet {
            print("number had old value \(oldValue)")
        }
        willSet {
            print("number will have new value \(newValue)")
        }
    }
    number = 2
    ```
    Output:
    ```
    number will have new value 2
    number had old value 0
    ```
2. Event Handlers
    - Using event handler in Swift, to be more specific in iOS is easy. For example, if you have a button in storyboard, just open the Assistant Editor. Then control click drag the button into the ViewController class. Select Action in Connection. And name it something like "buttonClick". Then it will create a connection between the button and the code in the ViewController.
    - When the button is clicked, the code in the buttonClick method will execute.

    