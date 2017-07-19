---
#layout: post
title: "Overloaded Base Function"
date: 2017-07-13 17:20
author: escrowdis
comments: true
tags: [c++, overloaded, inheritance]
---

I have overloaded function in class Base.

Class Derived inherited class Base
and **ONLY** want to override one foo function. This will make other Base::foo function not
able to call.

So that's how I solve it: Add `using Base::foo;` in Derived. 
(placed before or after override foo is OK!)

```c++
class Base
{
    virtual void foo(void);
    virtual void foo(int i);
    virtual void foo(float f);
    virtual void foo std::string str);
}

class Derived : public Base
{
    using Base::foo; //< Add this line
    void foo(int i);
}

main(int argc, char** argv)
{
  Derived d;
  d.foo(1.2);    //< This will cause erro if using Base::foo is not added
}
```
