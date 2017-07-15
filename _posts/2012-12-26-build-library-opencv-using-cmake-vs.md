---
#layout: post
title: "Build Library OpenCV 2.4.3 - Using CMake, VS"
date: 2012-12-26 17:20
author: escrowdis
comments: true
tags: [cmake, library, opencv, visual studio, vs]
---
使用
- CMake 2.8.10.2
- Visual Studio 10

資料庫內要有 **CMakeLists.txt** 才能Make Library

舉例：

Make OpenCV 2.4.3

1. 使用SVN更新最新的資料庫或直接上OpenCV官網抓source code

2. CMake轉換 開一個新資料夾準備放build之後的資料庫

轉換成功之後 會出現 **.sln** 檔

3. Visual Studio 10進入，開.sln進入後 會發現 <b>ALL BUILD</b>，右鍵按<b>重建</b>即可=D

可以看這個 蠻有用的
<a href="http://docs.opencv.org/doc/tutorials/introduction/windows_install/windows_install.html#windows-installation">http://docs.opencv.org/doc/tutorials/introduction/windows_install/windows_install.html#windows-installation</a>

PS:目前另外一種方法尚未解決
使用CMake, cmd.exe, Mingw...etc 還沒搞懂@W@

<span style="font-size: large;">要熟悉</span>
<span style="font-size: large;">1. CMake</span>
<span style="font-size: large;">2. Mingw</span>
<span style="font-size: large;">3. SVN</span>
