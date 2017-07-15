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
1. 抓 [OpenCV](http://opencv.org/downloads.html)
Go and download OpenCV

2. 抓出要的東西 有bin, doc, include, lib, samples [不一定].<br>
There're somethings that you need to copy out: 'bin', 'doc', 'include', 'lib', 'samples [optional]'.

3. Qt creator開新專案
Go to Qt creator and create a new project.

4. ".pro" 內輸入
Type the codes below into your** '.pro'** file
### OpenCV dir 路徑
`OpenCV_Lib = C:/OpenCV/opencv243/lib`

### 輸入需要的資料庫 (add the libraries needed or want)
```
INCLUDEPATH += C:/OpenCV/opencv243/include \
               C:/OpenCV/opencv243/include/opencv2
```

PS: 如果把opencv2資料夾裡面的opencv.hpp拉出來，
就只需要寫 (Type below if drag file '**opencv.hpp'** in folder opencv2 out to folder '**include'**)<br>
`INCLUDEPATH += C:/OpenCV/opencv243/include`

### 載入需要的資料庫 (load libraries)
```
Release: LIBS += $$OpenCV_Lib/opencv_highgui243.lib \
                 $$OpenCV_Lib/opencv_calib3d243.lib \
                 $$OpenCV_Lib/opencv_contrib243.lib \
                 $$OpenCV_Lib/opencv_core243.lib \
                 $$OpenCV_Lib/opencv_features2d243.lib \
                 $$OpenCV_Lib/opencv_flann243.lib \
                 $$OpenCV_Lib/opencv_gpu243.lib \
                 $$OpenCV_Lib/opencv_imgproc243.lib \
                 $$OpenCV_Lib/opencv_legacy243.lib \
                 $$OpenCV_Lib/opencv_ml243.lib \
                 $$OpenCV_Lib/opencv_objdetect243.lib \
                 $$OpenCV_Lib/opencv_ts243.lib \
                 $$OpenCV_Lib/opencv_video243.lib
```

這樣build之後就可以使用OpenCV資料庫拉~~~

Then run!
