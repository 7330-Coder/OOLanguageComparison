# Chapter 5 : Classes



### Defining
```Swift
class classname {
   Definition 1
   Definition 2
   ……
   Definition N
}
```

### Creating new instances
```Swift
class student{
   var studname: String
   var mark: Int 
   var mark2: Int 
   init(studname：String, mark:Int, mark2:Int){  
       self.studname=studname
       self.mark=mark
       self.mark2=mark2
    }  
}
```
```Swift
var s= student(studname: "Tiger", mark: 100, mark2: 200)
var ss=s
```

### Constructing / Initializing
Initializers are called to create a new instance of a particular type. In its simplest form, an initializer is like an instance method with no parameters, written using the init keyword:
```Swift
init() {
    // perform some initialization here
}
```


### Destructing / De-initializing
Swift automatically deallocates your instances when they are no longer needed, to free up resources. Swift handles the memory management of instances through automatic reference counting (ARC), as described in Automatic Reference Counting. Typically you don’t need to perform manual cleanup when your instances are deallocated. However, when you are working with your own resources, you might need to perform some additional cleanup yourself.
```Swift
class FileHandle {
   var fd: Int32
   init withFileDescriptor(fd: Int32) {
     self.fd = fd
   }
   deinit {
     close(fd)
   }
}

var f= FileHandle(fd: 1)
f.deinit()
```