---
title: Python Class Attribute and Instance Attribute pitfall
category: ['Python']
---

> If we use instance to modify the class attribute, it will create a instance attribute and not change the class attribute
{: .prompt-tip}

```py
>>> class A:
...     x = 1
... 
>>> a1 = A()
>>> a2 = A()
>>> a1.x = 5
>>> a2.x
1
>>> a3 = A()
>>> a3.x
1
>>> A.x = 10
>>> a1.x
5
>>> a2.x
10
>>> a3.x
10
```