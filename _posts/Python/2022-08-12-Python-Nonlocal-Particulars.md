---
title: 'Python Nonlocal Particulars'
categories: ['Python']
---

## Pre-compute

> Python **pre-computes** which frame contains each name before executing the body of a function. Within the body of a function, all instances of a name must refer to the same frame.
{: .prompt-tip}

```py
def make_withdraw(balance):
    def withdraw(amount):
        if amount > balance:
            return 'Insufficient funds'
        balance = balance - amount
        return balance
    return withdraw

>>> wd = make_withdraw(100)
>>> wd(10)
Traceback:
    if amount > balance:
UnboundLocalError: local variable 'balance' referenced before assignment
```
> Python **pre-computes** and finds there is a assignment statement 'balance = balance - amount', so all of 'balance' refer to the local variable.
{: .prompt-tip}

## Mutable Values

> Mutable values can be changed without a nonlocal statement.
{: .prompt-tip}

```py
def make_withdraw(balance):
    b = [balance]
    def withdraw(amount):
        if amount > b[0]:
            return 'Insufficient funds'
        b[0] = b[0] - amount
        return b[0]
    return withdraw

>>> wd = make_withdraw(100)
>>> wd(10)
90
>>> wd(20)
70
```

> We can think that variable 'b' always stores the same list using like address.
{: .prompt-tip}