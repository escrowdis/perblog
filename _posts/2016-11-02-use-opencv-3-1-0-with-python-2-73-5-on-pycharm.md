---
#layout: post
title: "Use OpenCV 3.1.0 with Python 2.7/3.5 on PyCharm"
date: 2016-11-02 07:11
author: escrowdis
comments: true
tags: [opencv, opencv-3.1.0, pycharm, python-2.7, python-3.5]
---
### For Python 2.7
<ol>
 	<li>Met some problem to apply built cv2.pyd to python 2.7. So just down the binary file from<strong><a href="http://opencv.org/downloads.html" target="_blank"> OpenCV download page</a></strong></li>
</ol>

### For Python 3.5

IF you haven't done with opencv, check post named **"build-opencv-3-1-0-with-python-2-73-5-and-numpy-on-windows-10-64-bit/"**to build it now.
<ol>
 	<li>Add OpenCV to system path first (ex: C:\opencv3.1.0\bin)</li>
 	<li>Copy the file '<strong>cv2.XXX.pyd</strong>' in OpenCV folder (ex: 'C:\opencv3.1.0\lib\python3\Release\cv2.cp35-win_amd64.pyd', if can't find it, just search with 'cv2*.pyd') to '<strong>C:\Program Files\Python35\DLLs</strong>' &amp; '<strong>C:\Program Files\Python35\Lib\site-packages</strong>' and rename it as <strong>cv2.pyd</strong></li>
 	<li>Create a project on PyCharm, try 'import cv2'.</li>
</ol>
ref.: <a href="http://stackoverflow.com/questions/32660114/how-to-install-opencv-on-windows-and-enable-it-for-pycharm-without-using-the-pac" target="_blank">http://stackoverflow.com/questions/32660114/how-to-install-opencv-on-windows-and-enable-it-for-pycharm-without-using-the-pac</a>
