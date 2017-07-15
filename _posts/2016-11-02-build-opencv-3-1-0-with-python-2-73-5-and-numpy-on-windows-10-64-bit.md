---
#layout: post
title: "Build OpenCV 3.1.0 with Python 2.7/3.5 and numpy on Windows 10 64 bit"
date: 2016-11-02 06:47
author: escrowdis
comments: true
tags: [build, cmake, numpy, opencv, python-2.7, python-3.5, windows10]
---
[NOTE] If you want to use OpenCV 3.1.0 with Python 2.7 only, just download the binary file from <a href="http://opencv.org/downloads.html" target="_blank">OpenCV</a>. It's already built the lib for python 2.7!

1. Download and install <strong>python 2.7/3.5</strong> (get them from <a href="https://www.python.org/downloads/" target="_blank">https://www.python.org/downloads/</a>)

2. Download and install an <strong>IDE</strong> for python, ex: Eclipse, PyCharm, Anaconda python...etc. This will be used in [](./use-opencv-3-1-0-with-python-2-73-5-on-pycharm.md) to teach how to use opencv-python

3. Get source code of OpenCV. There're many ways to achieve this:

a) Download and unzip <strong>OpenCV 3.1.0</strong> with source code and build (get it from <a href="http://opencv.org/downloads.html" target="_blank">http://opencv.org/downloads.html</a>)

b) use git on terminal to get <code>git clone https://github.com/opencv/opencv.git</code> and then <code>git checkout 3.1.0</code>

4. Add python directory to System path, <strong>Win + R</strong>, type '<strong>SystemPropertiesAdvanced</strong>'. Click the right-left button '<strong>Environmental variable</strong>' and <strong>edit</strong> the '<strong>Path</strong>' in <em>system parameter</em>. Add python's directories inside shown below (ex: add '<strong><em>C:\Program Files\Python35\Scripts;C:\Program Files\Python35;C:\Python27\Scripts;C:\Python27;</em></strong>')

systempropertiesadvanced

(you can add the path in these ways)

![]({{ site.url }}/images/posts/python-sys-path-1.png)
![]({{ site.url }}/images/posts/python-sys-path.png)

5. Go to python 3 folder, <strong>Shift + right-click</strong> to open <em>terminal</em>, then type '<em><strong>pip install numpy</strong></em>' and wait (if there's need an upgrade showed up, just follow the instruction).<strong> Installed python and numpy successfully.</strong>

![]({{ site.url }}/images/posts/python-install-numpy.png)

6. Open CMake gui and select

a) <strong>Where is the source code</strong>: the directory where contains <strong>CMakeList</strong> ('where-is-opencv-folder/sources' ex: 'C:\Users\User\Downloads\opencv\sources')

![]({{ site.url }}/images/posts/source-folder.png)

b) <strong>Where to build the binaries</strong>: choose a folder to put binaries. (ex: C:\Users\User\Downloads\opencv\bb)

7. <strong>Configure</strong> (choose compiler you want, for me it's VS 2015 a.k.a. VC++ 14) to check the parameters you like. I like to disable all the examples and gpu(not needed right now). By the <strong><a href="http://docs.opencv.org/3.1.0/d5/de5/tutorial_py_setup_in_windows.html" target="_blank">ref.</a></strong>, remember to DISABLE <b>ENABLE_SOLUTION_FOLDERS</b>'. (You can change the directory for built OpenCV in cmake '<strong>CMAKE_INSTALL_PREFIX</strong>')

8. <strong>Generate</strong>

![]({{ site.url }}/images/posts/cmake-gui.png)

8. After generate without error, open it in VS. Choose the mode you want upon the tool bar (ex: Debug/Release) and then <strong>right-click</strong> '<strong>ALL_BUILD</strong>' and choose <b>build</b>

9. Rebuild without error then right-click '<strong>INSTALL</strong>' to <strong>build</strong> it

![]({{ site.url }}/images/posts/all_build-success.png)

10. <strong>DONE!</strong> It's in the folder 'install' where you build your binaries.

11. I'll put: all the files in folder 'install', bin, and lib into 1 folder (C:\opencv3.1.0)  for use.

![]({{ site.url }}/images/posts/built-opencv.png)
