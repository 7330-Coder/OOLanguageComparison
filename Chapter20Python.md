# Chapter 20 : Multithreading (Python)

## Threads or thread-like abilities
`_thread` module and `threading` module are often used in working with threads in Python. `_thread` module provides low-level primitives for working with multiple threads. The `threading` module provides a more powerful and higher-level threading interfaces built on top of the `_thread` module. 
`threading` is availabel after Python 2.4 , it exposes all the methods of the `_thread` module and provides some additional methods.
- `threading.activeCount()`
	
	Returns the number of thread objects that are active.

- `threading.currentThread()`

	Returns the number of thread objects in the caller's thread control.

- `threading.enumerate()`

	Returns a list of all thread objects that are currently active.

In addition, `threading` module has the `Thread` class that implements threading. The methods provided by the `Thread` class are:
- `run()`
	
	Entry of a thread.

- `start()`

	Starts a thread by calling the `run()` method

- `join([time])`

	Waits for threads to terminate.

- `isAlive()`

	Checks whether a thread is still executing.

- `getName()`

	Returns the name of a thread.

- `setName()`

	Sets the name of a thread.

The steps to implement a new thread using `threading` module are as follows:
1. Define a new subclass of the `Thread` class.
2. Override the `__init__` method.
3. Override the `__run__` method to implement the tasks of a thread.
3. Once the subclass of `Thread` is created. Define an instance of it and then start a new thread by calling `start()`.

The threading module provided with Python includes a simple-to-implement locking mechanism allowing thread synchronization. The `acquire([blocking])` function of the new lock object is used to force threads to run synchronously. The optional `blocking` parameter enables control whether thread should waits to acquire the lock or not. The `release()` function is used to release the lock. The example code of synchronizing threads are as follows:
```python
import threading
import time


class MyThread(threading.Thread):

    def __init__(self, thread_id, name, counter):
        threading.Thread.__init__(self)
        self.threadID = thread_id
        self.name = name
        self.counter = counter

    def print_time(self, flag):
        while flag:
            time.sleep(self.counter)
            print("%s: %s" % (self.name, time.ctime(time.time())))
            flag -= 1

    def run(self):
        print("Starting " + self.name)
        threadLock.acquire()            # Set lock synchronize threads
        self.print_time(5)
        print("Exiting " + self.name)
        threadLock.release()            # Free lock to release next thread


threadLock = threading.Lock()
threads = []

thread1 = MyThread(1, "Thread-1", 1)
thread2 = MyThread(2, "Thread-2", 2)

thread1.start()
thread2.start()

# Add threads to thread list
threads.append(thread1)
threads.append(thread2)

# Wait for all threads to complete
for t in threads:
    t.join()
```
The output would be:
```
Starting Thread-1
Starting Thread-2
Thread-1: Thu Apr 19 14:41:54 2018
Thread-1: Thu Apr 19 14:41:55 2018
Thread-1: Thu Apr 19 14:41:56 2018
Thread-1: Thu Apr 19 14:41:57 2018
Thread-1: Thu Apr 19 14:41:58 2018
Exiting Thread-1
Thread-2: Thu Apr 19 14:42:00 2018
Thread-2: Thu Apr 19 14:42:02 2018
Thread-2: Thu Apr 19 14:42:04 2018
Thread-2: Thu Apr 19 14:42:06 2018
Thread-2: Thu Apr 19 14:42:08 2018
Exiting Thread-2
```

## How is multitasking accomplished?

`multiprocessing` is a package that supports spawning processes using an API similar to the `threading` module. It offers both local and remote concurrency and remote concurrency, effectively side-stepping the Global Interpreter Lock by using subprocesses instead of threads. Thus, this module allows fully leveraging multiple processors on a given machine.
A prime example of `multiprocessing` is the `Pool` object which offers a convenient approach to parallelize the execution of a function across multiple input values, distributing the input data across processes.
This basic example of data parallelism using `Pool`:
```python
import time
import urllib2
from multiprocessing.dummy import Pool as ThreadPool

urls = [
    'http://www.python.org',
    'http://www.python.org/about/',
    'http://www.onlamp.com/pub/a/python/2003/04/17/metaclasses.html',
    'http://www.python.org/doc/',
    'http://www.python.org/download/',
    'http://www.python.org/getit/',
    'http://www.python.org/community/',
    'https://wiki.python.org/moin/',
    'http://planet.python.org/',
    'https://wiki.python.org/moin/LocalUserGroups',
    'http://www.python.org/psf/',
    'http://docs.python.org/devguide/',
    'http://www.python.org/community/awards/'
    # etc..
]

start = time.time()
# Make the Pool of workers
pool = ThreadPool(1)
# Open the urls in their own threads
# and return the results
results = pool.map(urllib2.urlopen, urls)
# close the pool and wait for the work to finish
pool.close()
pool.join()

end = time.time()
elapsed = end - start

print("Time : " + str(elapsed))
```
The output time using different pool size would be:
```
Time : 3.69400000572    # Pool Size = 1 
Time : 1.44499993324    # Pool Size = 4 
Time : 1.26099991798    # Pool Size = 8
Time : 1.05399990082    # Pool Size = 16
```
`multiprocessing` contains equivalents of all the synchronization primitives from `threading`. For instance, one can use a lock to ensure that only one process prints to standard output at a time. The code block below shows a synchronization between processes:
```python
from multiprocessing import Process, Lock


def f(l, i):
    l.acquire()
    print('hello world', i)
    l.release()


if __name__ == '__main__':
    lock = Lock()
    for num in range(10):
        Process(target=f, args=(lock, num)).start()
``` 
The output would be:
```python
hello world 0
hello world 2
hello world 4
hello world 1
hello world 3
hello world 5
hello world 7
hello world 6
hello world 8
hello world 9
```

## Reference
[_Python Multithreaded Programming Tutorials_](https://www.tutorialspoint.com/python/python_multithreading.htm)

[_Python Official Documentation_](https://docs.python.org/2/library/multiprocessing.html)
