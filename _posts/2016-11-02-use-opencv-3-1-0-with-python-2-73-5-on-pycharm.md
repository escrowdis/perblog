---
#layout: post
title: "Use OpenCV 3.1.0 with Python 2.7/3.5 on PyCharm on Windows 10"
date: 2016-11-02 07:11
author: escrowdis
comments: true
tags: [opencv, opencv-3.1.0, pycharm, python-2.7, python-3.5, windows 8]
---
## For Python 2.7
Met some problem to apply built cv2.pyd to python 2.7. So just down the binary file from [OpenCV download page](http://opencv.org/downloads.html)

## For Python 3.5
IF you haven't done with opencv, check post named [build-opencv-3-1-0-with-python-2-73-5-and-numpy-on-windows-10-64-bit]({{ site.url}}/posts/build-opencv-3-1-0-with-python-2-73-5-and-numpy-on-windows-10-64-bit.html) to build it now.

1. Add OpenCV to system path first (ex: C:\opencv3.1.0\bin)

2. Copy the file '**cv2.XXX.pyd**' in OpenCV folder (ex: 'C:\opencv3.1.0\lib\python3\Release\cv2.cp35-win_amd64.pyd'. If can't find it, just search with '**cv2*.pyd**') into:<br>
'C:\Program Files\Python35\DLLs'<br>
'C:\Program Files\Python35\Lib\site-packages' and rename it as cv2.pyd

3. Create a project on PyCharm, try 'import cv2'.

[ref.](http://stackoverflow.com/questions/32660114/how-to-install-opencv-on-windows-and-enable-it-for-pycharm-without-using-the-pac)
