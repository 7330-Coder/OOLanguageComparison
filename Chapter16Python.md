# Chapter16 Chapter 16: Implementation of listeners and event handlers

## Python

The most basic style of event system is the 'bag of handler methods', which is a simple implementation of the [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern). Basically, the handler methods (callables) are stored in an array and are each called when the event 'fires'.
* [zope.event](https://pypi.python.org/pypi/zope.event) shows the bare bones of how this works (see [details](http://stackoverflow.com/questions/1092531/event-system-in-python/1092617#1092617)). Note: this example does not even support handler arguments.

* [LongPoke's 'callable list'](http://stackoverflow.com/questions/1092531/event-system-in-python/2022629#2022629) implementation shows that such an event system can be implemented very minimalistically by subclassing `list`.

* [Josip's Valued Lessons Event class](http://stackoverflow.com/questions/1092531/event-system-in-python/1096614#1096614) is basically the same, but uses a `set` instead of a `list` to store the bag, and implements `__call__` which are both reasonable additions. The following shows the implementation:

* [PyNotify](http://home.gna.org/py-notify/) is similar in concept and also provides additional concepts of variables and conditions ('variable changed event').

* [axel](https://pypi.python.org/pypi/axel) is basically a bag-of-handlers with more features related to threading, error handling, ...

The disadvantage of these event systems is that you can only register the handlers on the actual Event object (or handlers list). So at registration time the event already needs to exist.

That's why the second style of event systems exists: the [publish-subscribe pattern](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern). Here, the handlers don't register on an event object (or handler list), but on a central dispatcher. Also the notifiers only talk to the dispatcher. What to listen for, or what to publish is determined by 'signal', which is nothing more than a name (string).

* [blinker](https://pythonhosted.org/blinker/) has some nifty features such as automatic disconnection and filtering based on sender.
* [PyPubSub](https://github.com/schollii/pypubsub) at first sight seems to be pretty straightforward; apparently does not yet support Python3.

* [PyDispatcher](http://pydispatcher.sourceforge.net/) seems to emphasize flexibility with regards to many-to-many publication etc.

* [louie](https://github.com/11craft/louie) is a reworked PyDispatcher "providing plugin infrastructure including Twisted and PyQt specific support".
* [django.dispatch](https://github.com/django/django/tree/master/django/dispatch) is a rewritten PyDispatcher "with a more limited interface, but higher performance".


* Qt's Signals and Slots are available from [PyQt](http://pyqt.sourceforge.net/Docs/PyQt4/new_style_signals_slots.html) or [PySide](https://wiki.qt.io/Signals_and_Slots_in_PySide). They work as callback when used in the same thread, or as events (using an event loop) between two different threads. Signals and Slots have the limitation that they only work in objects of classes that derive from `QObject`.

Note: `threading.Event` is not an 'event system' in the above sense. It's a thread synchronization system where one thread waits until another thread 'signals' the Event object.


Here is an example of using an EventHook as suggested from Event Pattern:
Just add EventHooks to your classes with:
```Python
class MyBroadcaster()
    def __init__():
        self.onChange = EventHook()

theBroadcaster = MyBroadcaster()

# add a listener to the event
theBroadcaster.onChange += myFunction

# remove listener from the event
theBroadcaster.onChange -= myFunction

# fire event
theBroadcaster.onChange.fire()
```
We add the functionality to remove all listener from an object to Michaels class and ended up with this:
class EventHook(object):
```Python
    def __init__(self):
        self.__handlers = []

    def __iadd__(self, handler):
        self.__handlers.append(handler)
        return self

    def __isub__(self, handler):
        self.__handlers.remove(handler)
        return self

    def fire(self, *args, **keywargs):
        for handler in self.__handlers:
            handler(*args, **keywargs)

    def clearObjectHandlers(self, inObject):
        for theHandler in self.__handlers:
            if theHandler.im_self == inObject:
                self -= theHandler
```


Here is another example of using zope.event:
```Python
subscribers = []

def notify(event):
    for subscriber in subscribers:
        subscriber(event)
```


### Citation
My answer comes from [answer to this question](https://stackoverflow.com/questions/1092531/event-system-in-python)























