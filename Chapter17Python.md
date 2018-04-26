# Chapter 17: Singleton

## Python

### How is a singleton implemented?

Simple implement in Python(not threasd safe)  
```python
    class Singleton(object):
        __instance = None

        def __init__(self):
            pass

        def __new__(cls, *args, **kwargs):
            if not cls.__instance:
                cls.__instance = super(Singleton, cls).__new__(cls, *args, **kwargs)
            return cls.__instance

    if __name__ == "__main__":
        instance1 = Singleton()
        instance2 = Singleton()

        print id(instance1)
        print id(instance2)
		
```

#### Here are some best methods：

###### Method 1: A decorator

```python
def singleton(class_):
  instances = {}
  def getinstance(*args, **kwargs):
    if class_ not in instances:
        instances[class_] = class_(*args, **kwargs)
    return instances[class_]
  return getinstance

@singleton
class MyClass(BaseClass):
  pass
```


###### Method 2: A base class

```python
class Singleton(object):
  _instance = None
  def __new__(class_, *args, **kwargs):
    if not isinstance(class_._instance, class_):
        class_._instance = object.__new__(class_, *args, **kwargs)
    return class_._instance

class MyClass(Singleton, BaseClass):
  pass
```


###### Method 3:

```python
class Singleton(type):
    _instances = {}
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super(Singleton, cls).__call__(*args, **kwargs)
        return cls._instances[cls]

#Python2
class MyClass(BaseClass):
    __metaclass__ = Singleton

#Python3
class MyClass(BaseClass, metaclass=Singleton):
    pass
```


###### Method 4: decorator returning a class with the same name

```python
def singleton(class_):
  class class_w(class_):
    _instance = None
    def __new__(class_, *args, **kwargs):
      if class_w._instance is None:
          class_w._instance = super(class_w,
                                    class_).__new__(class_,
                                                    *args,
                                                    **kwargs)
          class_w._instance._sealed = False
      return class_w._instance
    def __init__(self, *args, **kwargs):
      if self._sealed:
        return
      super(class_w, self).__init__(*args, **kwargs)
      self._sealed = True
  class_w.__name__ = class_.__name__
  return class_w

@singleton
class MyClass(BaseClass):
    pass
```


### Can it be made thread-safe?

A thread safe implementation of singleton pattern in Python. Based on tornado.ioloop.IOLoop.instance() approach.

```python
import threading

# Based on tornado.ioloop.IOLoop.instance() approach.
# See https://github.com/facebook/tornado
class SingletonMixin(object):
	__singleton_lock = threading.Lock()
	__singleton_instance = None

	@classmethod
	def instance(cls):
		if not cls.__singleton_instance:
			with cls.__singleton_lock:
				if not cls.__singleton_instance:
					cls.__singleton_instance = cls()
		return cls.__singleton_instance


if __name__ == '__main__':
	class A(SingletonMixin):
		pass

	class B(SingletonMixin):
		pass

	a, a2 = A.instance(), A.instance()
	b, b2 = B.instance(), B.instance()

	assert a is a2
	assert b is b2
	assert a is not b

	print('a:  %s\na2: %s' % (a, a2))
	print('b:  %s\nb2: %s' % (b, b2))
```
You can view the original website from [werediver](https://gist.github.com/werediver) 


### Can the singleton instance be lazily instantiated?

**Yes!** 

Here is an example：

```python
class Singleton:
    __instance = None
    def __init__(self):
        if not Singleton.__instance:
            print(" __init__ method called..")
        else:
            print("Instance already created:", self.getInstance())
    @classmethod
    def getInstance(cls):
        if not cls.__instance:
            cls.__instance = Singleton()
        return cls.__instance


s = Singleton() ## class initialized, but object not created
print("Object created", Singleton.getInstance()) # Object  # Object gets created here
s1 = Singleton() ## instance already created
```