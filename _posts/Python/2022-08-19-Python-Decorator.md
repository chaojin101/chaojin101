---
title: Python Decorator
categories: ['Python']
---

Here I will show how to write a decorator. Knowing how to write a decorator makes me know what is decorator.

in temp.py
```py
def count(f):
    def counted(*args):
        counted.call_count += 1
        return f(*args)
    counted.call_count = 0
    return counted

@count
def fib(n):
    if n == 0 or n == 1:
        return n
    return fib(n-2) + fib(n-1)
```
```sh
python -i temp.py
```
```py
>>> fib(2)
1
>>> fib.call_counted
3
```

If without @count, 

in temp.py
```py
def count(f):
    def counted(*args):
        counted.call_count += 1
        return f(*args)
    counted.call_count = 0
    return counted

def fib(n):
    if n == 0 or n == 1:
        return n
    return fib(n-2) + fib(n-1)
```
```sh
python -i temp.py
```
```py
>>> fib = count(fib)  # equal @count before def
>>> fib(2)
1
>>> fib.call_count
3
```