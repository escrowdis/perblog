---
#layout: post
title: "pragma pack caused core dump/segmentation fault issue"
description: "Memeory Alignment Problem"
date: 2017-04-20 00:23
author: escrowdis
comments: true
tags: [pack, memory_alignment]
---
Today is a long day because my colleagues and I spent lots of times debugging. We've tried to use v4l2 to capture image from camera and display using OpenCV.

But we met a problem is no matter how we call any cv functions, the program went core dump kind of crash. Finally we solved it by tracking a class using
```c++
#pragma pack(1)
```

It's the way to **guide compiler to pack structure with specific alignment** (let processor easier to grab data with less access).
 
**Note**: The default pack is 16 under x64 bit processor now.

Ref.:
- [ref1](https://msdn.microsoft.com/en-us/library/2e70t5y1.aspx)
- [ref2](https://read01.com/GAmyO.html)
- [ref3](http://stackoverflow.com/questions/3318410/pragma-pack-effect)
- [ref4](http://nvd11.blog.163.com/blog/static/200018312201312484316245/)
