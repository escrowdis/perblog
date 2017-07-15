---
#layout: post
title: "Build OpenCV 3.1.0 with Python 2.7/3.5 and numpy on Windows 10 64 bit"
date: 2016-11-02 06:47
author: escrowdis
comments: true
tags: [build, cmake, numpy, opencv, python-2.7, python-3.5, windows10]
---
## Preface
If you want to use OpenCV 3.1.0 with Python 2.7 only, just download the binary file from [OpenCV](http://opencv.org/downloads.html). It's already built the lib for python 2.7!

1. Download and install **python 2.7/3.5** (get them from [here](https://www.python.org/downloads/))

2. Download and install an **IDE** for python (ex: Eclipse, PyCharm, Anaconda python...etc). This will be used in [this post]({{ site.url }}/posts/use-opencv-3-1-0-with-python-2-73-5-on-pycharm.md) to teach how to use opencv-python

3. Get source code of OpenCV. There're many ways to achieve this:
  - Download and unzip [OpenCV 3.1.0](http://opencv.org/downloads.html) with source code and build.
  - use git on terminal to get OpenCV source code<br>
`git clone https://github.com/opencv/opencv.git <folder-name-to-store>`<br>
And then checkout version you want<br>
`git checkout 3.1.0`

4. Add python directory to System path<br>
open terminal with **Win + R**, type '**SystemPropertiesAdvanced**'.<br>
Click the right-left button '**Environmental variable**' and **edit** the '**Path**' in *system parameter*.<br>
Add python's directories inside shown below (ex: add '*C:\Program Files\Python35\Scripts;C:\Program Files\Python35;C:\Python27\Scripts;C:\Python27;*')

systempropertiesadvanced
(you can add the path in these ways)<br>
![]({{ site.url }}/images/posts/python-sys-path-1.png)<br>
![]({{ site.url }}/images/posts/python-sys-path.png)

5. Go to python 3 folder, **Shift + right-click** to open *terminal*, then type '***pip install numpy***' and wait (if there's need an upgrade showed up, just follow the instruction).** Installed python and numpy successfully.**

![]({{ site.url }}/images/posts/python-install-numpy.png)

6. Open CMake gui and select

a) **Where is the source code**: the directory where contains **CMakeList** ('where-is-opencv-folder/sources' ex: 'C:\Users\User\Downloads\opencv\sources')

![]({{ site.url }}/images/posts/source-folder.png)

b) **Where to build the binaries**: choose a folder to put binaries. (ex: C:\Users\User\Downloads\opencv\bb)

7. **Configure** (choose compiler you want, for me it's VS 2015 a.k.a. VC++ 14) to check the parameters you like. I like to disable all the examples and gpu(not needed right now). By the [reference](http://docs.opencv.org/3.1.0/d5/de5/tutorial_py_setup_in_windows.html), remember to DISABLE <b>ENABLE_SOLUTION_FOLDERS</b>'. (You can change the directory for built OpenCV in cmake '**CMAKE_INSTALL_PREFIX**')

8. **Generate**

![]({{ site.url }}/images/posts/cmake-gui.png)

8. After generate without error, open it in VS. Choose the mode you want upon the tool bar (ex: Debug/Release) and then **right-click** '**ALL_BUILD**' and choose <b>build</b>

9. Rebuild without error then right-click '**INSTALL**' to **build** it

![]({{ site.url }}/images/posts/all_build-success.png)

10. **DONE!** It's in the folder 'install' where you build your binaries.

11. I'll put: all the files in folder 'install', bin, and lib into 1 folder (C:\opencv3.1.0)  for use.

![]({{ site.url }}/images/posts/built-opencv.png)
