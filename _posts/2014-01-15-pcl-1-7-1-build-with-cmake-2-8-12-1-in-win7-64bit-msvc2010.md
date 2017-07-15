---
#layout: post
title: "PCL 1.7.1 build with CMake 2.8.12.1 in Win7 64bit, MSVC2010"
date: 2014-01-15 10:11
author: escrowdis
comments: true
tags: [64bit, CMake, CMake 2.8.12.1, PCL, PCL 1.7.1, Programming, Win, Win 7, Windows]
---
### Preparation
First of all, My computer platform is:

1. MSVC 2010
2. CMake 2.8.12.1
3. Flann, Eigen, VTK 5.8.0, Boost 1.55
    - Download flann and eigen from [here](http://pointclouds.org/downloads/))
    - If you don't want to build Boost yourself, you can go **"boost-binaries"** folder and [download](http://sourceforge.net/projects/boost/files/).<br>
    The [official website](http://www.boost.org/) also provides the source code
    - [VTK](http://www.vtk.org/VTK/resources/software.html): This is easy to build, just click what you need when building with CMake.
4. PCL source code
    - If you want to get the new release version, you can download it from [Github](https://github.com/PointCloudLibrary/pcl).

![]({{ site.url }}/images/posts/321.png)

```
cd wherever-to-put-repo
git clone https://github.com/PointCloudLibrary/pcl.git
```

- - -
After download it, let's use CMake to build it! The following steps will teach you how to build it.
<br>
1. [Compiling PCL from source on Windows](http://pointclouds.org/documentation/tutorials/compiling_pcl_windows.php)
<br>
2. [Compiling from source](http://www.pointclouds.org/downloads/source.html)
<br>
 [Using PCL in your own project](http://pointclouds.org/documentation/tutorials/using_pcl_pcl_config.php#using-pcl-pcl-config)

### Building steps
[Follow this site's steps](http://pointclouds.org/documentation/tutorials/compiling_pcl_windows_3rdparty_installers.php#compiling-pcl-windows-3rdparty-installers)

Then you'll build it successfully !!!

For me, there are many problems during building it...<br>
<b>I replaced:<br>
**[Due to Boost version problem]**<br>
C:Qt4.8.0 => C:Qt4.8.4<br>
**[CMake detect the wrong Dir of PerC SDK]**<br>
- **.vcxproj =>** DEBUG path: ".lib" -> "_d.lib"<br>
- **Win bit problem:** "libx64" -> "libWin32"<br>

**[Maybe Qt version confliction?]**<br>
**filter_indices.h =>** comment this line: "using Filter<PointT>::applyFilter;"
[ref](http://www.pcl-users.org/Build-error-with-latest-source-td4031369.html#a4031429).

If you need OpenGL, then get it from here~
[OpenGL (GLEW)](http://surflab.cise.ufl.edu/wiki/Getting_Started_with_OpenGL_in_VisualC%2B%2B_2010)
