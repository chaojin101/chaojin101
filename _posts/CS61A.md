---
title: CS61A Note
categories: ["CS61A"]
tags: ["CS61A"]
math: true
pin: true
---

Official Website 2020: <https://inst.eecs.berkeley.edu/~cs61a/su20/>

### lab03 Q4: Repeated, repeated
In Homework 2 you encountered the **repeated** function, which takes arguments **f** and **n** and returns a function equivalent to the nth repeated application of **f**. This time, we want to write **repeated** recursively. You'll want to use **compose1**, given below for your convenience:
```python
def compose1(f, g):
    """"Return a function h, such that h(x) = f(g(x))."""
    def h(x):
        return f(g(x))
    return h
```
```py
def repeated(f, n):
    """Return the function that computes the nth application of func (recursively!).

    >>> add_three = repeated(lambda x: x + 1, 3)
    >>> add_three(5)
    8
    >>> square = lambda x: x ** 2
    >>> repeated(square, 2)(5) # square(square(5))
    625
    >>> repeated(square, 4)(5) # square(square(square(square(5))))
    152587890625
    >>> repeated(square, 0)(5)
    5
    >>> from construct_check import check
    >>> # ban iteration
    >>> check(HW_SOURCE_FILE, 'repeated',
    ...       ['For', 'While'])
    True
    """
    "*** YOUR CODE HERE ***"
```
Use Ok to test your code:
```sh
python3 ok -q repeated
```

In the beginning, I didn't use **compose1**, and didn't repeat the **repeated**. Here is the code:
```py
def repeated(f, n):
    def repeater(x):
        nonlocal n
        if n == 0:
            return x
        n -= 1
        x = f(x)
        return repeater(x)
    return repeater
```

After a while, I find I can use **compose1** to use one **f**, and reduce n.
```py
def repeated(f, n):
    if n == 0:
        return lambda x: x
    return compose1(repeated(f, n-1), f)
```