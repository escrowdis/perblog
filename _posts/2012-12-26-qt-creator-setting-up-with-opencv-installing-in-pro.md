---
#layout: post
title: "[Qt creator] setting up with OpenCV (Installing in .pro)"
date: 2012-12-26 15:22
author: escrowdis
comments: true
tags: [.pro, creator, environment, opencv, qt_creator]
---
目前將OpenCV載入Qt creator都是同樣的方法

使用
- Qt creator 2.4.0
- Qt Libraries 4.8.2

掛載過 OpenCV 2.3, OpenCV 2.4, OpenCV 2.4.3 都OK

# Steps
1. <a href="http://opencv.org/downloads.html">http://opencv.org/downloads.html</a>   抓OpenCV
Go and download OpenCV

2. 抓出要的東西 有bin, doc, include, lib, samples [不一定].

There're somethings that you need to copy out: 'bin', 'doc', 'include', 'lib', 'samples [optional]'.

3. Qt creator開新專案
Go to Qt creator and create a new project.

4. "<b>.pro</b>"內輸入
Type the codes below into your<strong> '.pro'</strong> file
<h4></h4>
<h4>OpenCV dir 路徑</h4>
<code>OpenCV_Lib = C:/OpenCV/opencv243/lib</code>
<h4></h4>
<h4>輸入需要的資料庫 (add the libraries needed or want)</h4>
<code><span style="color: #008000;">INCLUDEPATH </span>+= C:/OpenCV/opencv243/<span style="color: #ff6600;">include</span>
C:/OpenCV/opencv243/<span style="color: #ff6600;">include</span>/opencv2</code>

PS: 如果把opencv2資料夾裡面的opencv.hpp拉出來，就只需要寫 (Type below if drag file '<strong>opencv.hpp'</strong> in folder opencv2 out to folder '<strong>include'</strong>)

<code><span style="color: #008000;">INCLUDEPATH </span>+= C:/OpenCV/opencv243/<span style="color: #ff6600;">include</span></code>

&nbsp;
<h4>載入需要的資料庫 (load libraries)</h4>
<code>Release: <span style="color: #55ff55;">LIBS</span> += $$OpenCV_Lib/opencv_highgui243.lib
$$OpenCV_Lib/opencv_calib3d243.lib
$$OpenCV_Lib/opencv_contrib243.lib
$$OpenCV_Lib/opencv_core243.lib
$$OpenCV_Lib/opencv_features2d243.lib
$$OpenCV_Lib/opencv_flann243.lib
$$OpenCV_Lib/opencv_gpu243.lib
$$OpenCV_Lib/opencv_imgproc243.lib
$$OpenCV_Lib/opencv_legacy243.lib
$$OpenCV_Lib/opencv_ml243.lib
$$OpenCV_Lib/opencv_objdetect243.lib
$$OpenCV_Lib/opencv_ts243.lib
$$OpenCV_Lib/opencv_video243.lib</code>

這樣build之後就可以使用OpenCV資料庫拉~~~

Then run!
