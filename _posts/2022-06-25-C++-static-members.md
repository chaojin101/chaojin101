---
title: C++ static members note
categories: ["C++"]
---
premise:
- Static members in a class.

note:
- The `static` keyword is only used with the declaration of a static member, inside the class definition, but not with the definition of that static member;
```cpp
class X {
public: 
    static int n;    // declaration, incomplete type
    static void f(); // declaration, incomplete type
};
int X::n = 1;        // definition, complete type
void X::f() {n = 1;} // definition, complete type
```

- Static members obey the class member access rules (private, protected, public);

