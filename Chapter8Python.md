# Chapter 8 : Interfaces & Protocols (Python)

## What does the language support?
Interface is the description of how an object behaves. It specify what an object can do to paly it's role in a system and set clear boundaries to help us organize code better. However, there is no `interface` keyword in Python since it is a dynamic language. It focuses on how an object behaves, rather than it's role, or to say it's type/class.
>If it talks and walks like a duck, then it is a duck.
So any object, regardless of it’s role (class/type), can conform to a certain interface just by implementing the expected behavior (methods). These informal interfaces are termed as `protocols`. 

## What abilities does it have?
`Protocols` can not be formally enforced and they are mostly illustrated in the documentations or defined by convention. The following code is a simple example.
```python
class Team:
  def __int__(self, members):
    self._members = members
  def __len__(self, member):
    return len(self._members)
  def __contains__(self, member):
    return member in self._members

oo_final_project = Team(["Fan", "Siyang", "Yuhan", "Huanhuan"])
```
In this case, if directly try to iterate over the `Team` without implementing `__iter__` function, the error would be:
```python
TypeError: 'Team' object is not iterable
```
Above all, it is clearer to see that protocol is implemented in Python by implementing methods expected by it.

## How is it used?
The line below shows a sized protocol.
```python
print(len(oo_final_project))
```
The line below shows a container protocol.
```python
print("Huanhuan" in oo_final_project)
```

