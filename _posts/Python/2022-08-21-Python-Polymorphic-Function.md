---
title: 'Python Polymorphic Function'
categories: ['Python']
---
This is an example for polymorphy in python.

```py
class Bear:
    """A Bear."""
    def __init__(self):
        self.__repr__ = lambda: 'oski'
        self.__str__ = lambda: 'this bear'

    def __repr__(self):
        return 'Bear()'

    def __str__(self):
        return 'a bear'

oski = Bear()
print(oski)            # if have class function __str__, use __str__, else use __repr__
print(str(oski))       # class function
print(repr(oski))      # class function
print(oski.__str__())  # instance function
print(oski.__repr__()) # instance function
```
```
a bear
a bear
Bear()
this bear
oski
```
The implementation of built-in polymorphic functions **str()** and **repr()** are:
```py
class Bear:
    """A Bear."""
    def __init__(self):
        self.__repr__ = lambda: 'oski'
        self.__str__ = lambda: 'this bear'

    def __repr__(self):
        return 'Bear()'

    def __str__(self):
        return 'a bear'

def repr(x):
    return type(x).__repr__(x)

def str(x):
    t = type(x)
    if hasattr(t, '__str__'):
        return t.__str__(x)
    return t.__repr__(x)

oski = Bear()
print(oski)            # if have class function __str__, use __str__, else use __repr__
print(str(oski))       # class function
print(repr(oski))      # class function
print(oski.__str__())  # instance function
print(oski.__repr__()) # instance function
```
Actually, str is a class, str() is a constructor, using function have the same effect in this situation.

We can write our own polymorphic functions if multiple classes have the same behavior.