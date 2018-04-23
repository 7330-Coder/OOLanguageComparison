# Multithreading
1. Threads in Swift
   - Swift, to be more specific, iOS supports 3 kinds of multithreading technologies--Thread class, GCD, and Operation. The GCD and Operation are widely used in real App development.
   - Thread class is similar like NSThread class in Objective-C, which is an encapsulation of C language pthread.
   - GCD is written is language C. At the period when people use Objective-C, using GCD is just to call some C functions in the program. And this scenario didn't change until the introducing of Swift 3. Before Swift 3, using GCD in Swift is just like using it in Objective-C. But after that, Apple encapsulate the C functions into classes. Developer can use it through a more Object-Oriented way.
   - Operation is from Objective-C's NSOperation. It is an another encapsulation of GCD, that could be used in a more Object-Oriented way.
2. Programming for multithreading in Swift
   - GCD
     - There are two kind of queues in GCD--Concurrent queue and Serial queue. And there are also two type of methods--async method and sync method. Concurrent queues will execute tasks concurrently, whereas serial queues will execute task serially. Async method can open new thread, but sync method cannot. So, totally there are 4 combinations. See the Demo.
     - Current Queue + Async Method
     - ```Swift
        let queue = DispatchQueue(label: "com.myqueue1", qos: .default, attributes: .concurrent, autoreleaseFrequency: .inherit, target: nil)
        
        queue.async {
            print("task 1 in \(Thread.current)")
        }
        queue.async {
            print("task 2 in \(Thread.current)")
        }
        queue.async {
            print("task 3 in \(Thread.current)")
        }
       ```
       Output:
       ```
       task 2 in <NSThread: 0x60c000075940>{number = 5, name = (null)}
       task 1 in <NSThread: 0x604000262c80>{number = 3, name = (null)}
       task 3 in <NSThread: 0x60c000075880>{number = 4, name = (null)}
       ```
     - Current Queue + Sync Method
     - ```Swift
        let queue = DispatchQueue(label: "com.myqueue1", qos: .default, attributes: .concurrent, autoreleaseFrequency: .inherit, target: nil)
        
        queue.sync {
            print("task 1 in \(Thread.current)")
        }
        queue.sync {
            print("task 2 in \(Thread.current)")
        }
        queue.sync {
            print("task 3 in \(Thread.current)")
        }
       ```
       Output:
       ```
       task 1 in <NSThread: 0x60800007c000>{number = 1, name = main}
       task 2 in <NSThread: 0x60800007c000>{number = 1, name = main}
       task 3 in <NSThread: 0x60800007c000>{number = 1, name = main}
       ```
     - Serial Queue + Async Method
     - ```Swift
        let queue = DispatchQueue(label: "com.myqueue1", qos: .default, attributes: .init(rawValue: 0), autoreleaseFrequency: .inherit, target: nil)
        
        queue.async {
            print("task 1 in \(Thread.current)")
        }
        queue.async {
            print("task 2 in \(Thread.current)")
        }
        queue.async {
            print("task 3 in \(Thread.current)")
        }
       ```
       Output:
       ```
       task 1 in <NSThread: 0x600000073ac0>{number = 3, name = (null)}
       task 2 in <NSThread: 0x600000073ac0>{number = 3, name = (null)}
       task 3 in <NSThread: 0x600000073ac0>{number = 3, name = (null)}
       ```
     - Serial Queue + Sync Method
     - ```Swift
        let queue = DispatchQueue(label: "com.myqueue1", qos: .default, attributes: .init(rawValue: 0), autoreleaseFrequency: .inherit, target: nil)
        
        queue.sync {
            print("task 1 in \(Thread.current)")
        }
        queue.sync {
            print("task 2 in \(Thread.current)")
        }
        queue.sync {
            print("task 3 in \(Thread.current)")
        }
       ```
       Output:
       ```
       task 1 in <NSThread: 0x60c00006c040>{number = 1, name = main}
       task 2 in <NSThread: 0x60c00006c040>{number = 1, name = main}
       task 3 in <NSThread: 0x60c00006c040>{number = 1, name = main}
       ```
   - Operation
     - Operation is used to fine the code to be executed, tytically its subclass--BlockOperation is used.
     - OperationQueue is used to perform the Opertions. If main queue is used, it won't open new threads. Otherwise, it will open threads.
     - Open Threads
     - ```Swift
        let operation1 = BlockOperation {
            print("task 1 in \(Thread.current)")
        }
        let operation2 = BlockOperation {
            print("task 2 in \(Thread.current)")
        }
        let operation3 = BlockOperation {
            print("task 3 in \(Thread.current)")
        }
        
        let queue = OperationQueue()
        queue.addOperation(operation1)
        queue.addOperation(operation2)
        queue.addOperation(operation3)
       ```
       Output:
       ```
       task 3 in <NSThread: 0x60000007f480>{number = 3, name = (null)}
       task 2 in <NSThread: 0x60400007df00>{number = 4, name = (null)}
       task 1 in <NSThread: 0x608000078400>{number = 5, name = (null)}
       ```
     - Don't Open Threads (Run on Main Thread)
     - ```Swift
        let operation1 = BlockOperation {
            print("task 1 in \(Thread.current)")
        }
        let operation2 = BlockOperation {
            print("task 2 in \(Thread.current)")
        }
        let operation3 = BlockOperation {
            print("task 3 in \(Thread.current)")
        }
        
        let queue = OperationQueue.main
        queue.addOperation(operation1)
        queue.addOperation(operation2)
        queue.addOperation(operation3)
       ```
       Output:
       ```
       task 1 in <NSThread: 0x60c0002609c0>{number = 1, name = main}
       task 2 in <NSThread: 0x60c0002609c0>{number = 1, name = main}
       task 3 in <NSThread: 0x60c0002609c0>{number = 1, name = main}
       ```