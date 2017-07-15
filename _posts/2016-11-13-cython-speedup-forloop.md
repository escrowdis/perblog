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

And~ I found <strong><a href="http://docs.cython.org/en/latest/index.html" target="_blank">Cython</a>!</strong> There're many ways to compile by Cython (<a href="http://docs.cython.org/en/latest/src/quickstart/build.html" target="_blank">http://docs.cython.org/en/latest/src/quickstart/build.html</a>)
<ol>
 	<li>Download from <a href="http://docs.cython.org/en/latest/src/quickstart/install.html" target="_blank">web</a>, and open cmd in download folder. Type pip install Cython-0.25.1-cp35-none-win_amd64.whl</li>
 	<li>Go to folder contains target python code</li>
 	<li>python setup.py build_ext --inplace</li>
</ol>
ref.: <a href="http://docs.cython.org/en/latest/src/quickstart/build.html#building-a-cython-module-using-distutils" target="_blank">http://docs.cython.org/en/latest/src/quickstart/build.html#building-a-cython-module-using-distutils</a>

**Enhanced 23% up**
