# Chapter 3 : Name spaces



### How are name spaces implemented?
A namespace in Swift is a named region of a program. As such they provide virtual grouping within our code where things outside of the namespace cannot access things inside of the namespace without first mentioning the namespaces itself. This provides a virtual partitioning separating the names in one namespace from the names in another. It also allows two items to be declared with the same name as long as they are in different namespaces.

### How are name spaces used?
In Swift, unlike in some other languages, the declaration of namespaces is implicit. This means that we don’t explicitly declare namespaces for ourselves. Instead Swift creates a namespace at the boundary of each module. That means your code has it’s own namespace and any framework you write will have it’s own separate namespace. It also means that any frameworks that you import will also have their own namespaces, thereby avoiding the namespace clash 