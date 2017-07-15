---
#layout: post
title: "[Qt creator] Image | Windows Tips 視窗移動 大小"
date: 2013-02-08 05:42
author: escrowdis
comments: true
tags: [creator, image, Programming, Qt, Qt creator, window]
---
一般想直接開新視窗顯示圖片會用

`imshow("src", image_preview);`

每次重新開啟程式視窗位置總是要再調

現在簡單了   教一種方法<br>
一般會使用QWidget做調整~  這邊直接加functions就好

加上<br>
```c++
//讓視窗可自由變化，如果flag=WINDOW_AUTOSIZE則無法調大小
namedWindow("src", WINDOW_NORMAL);
imshow("src", image_preview);
//重新調整視窗大小 但比例要自己抓 不然圖會變形
resizeWindow("src", 600,450);
//調整視窗在螢幕中的位置
moveWindow("src", 650, 30);
```

結束拉～有沒有很簡單
