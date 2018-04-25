# Singleton
1. Singleton Implementation
    - One way to implement singleton is to create a static variable in the class named sharedXXX, and make the initializer private. For the outside, just use sharedXXX to get the instance of it.
      - Code Example
      ```Swift
      class Manager: NSObject {
          static var sharedManager = Manager()
          private override init() {
          }
      }
      ```
 2. Thread-safe method
    - The simgleton in swift can be made thread-saft using synchrionize. To use it just put all the code that could cause thread-unsafe between objc_sync_enter and objc_sync_exit.
      - Code Example
      ```Swift
      class Manager: NSObject {
          static var sharedManager = Manager()
              private override init() {
          }
          
          func doSomething() {
              objc_sync_enter(self)
              // do something here
              objc_sync_exit(self)
          }
      }
      ```
3. Lazy Inisitlization of Singleton
    - Lazy inisitlization of singleton is easy. Since static members of Swift classes are implicitly lazy, you don't need to do anything extra.