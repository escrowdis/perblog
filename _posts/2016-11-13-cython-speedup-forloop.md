---
#layout: post
title: "Cython to speed up python code in ForLoop with Python 3.5 on Windows 10 64bit"
date: 2016-11-13 15:38
author: escrowdis
comments: true
tags: [cython, python, for_loop]
---
I'm doing image processing with 3 nested for loop in Python, and everyone knows it's very slowly in ForLoop QAQ

So I tried to compile python code into c code to speed up.

And~ I found There're many ways to compile by [Cython](http://docs.cython.org/en/latest/index.html)

1. Download from [web](http://docs.cython.org/en/latest/src/quickstart/install.html), and open cmd at download folder. Type
`pip install Cython-0.25.1-cp35-none-win_amd64.whl`
2. Go to folder contains target python code
3. `python setup.py build_ext --inplace`

It works out to **Enhanced 23% up**

[Ref.](http://docs.cython.org/en/latest/src/quickstart/build.html#building-a-cython-module-using-distutils)
