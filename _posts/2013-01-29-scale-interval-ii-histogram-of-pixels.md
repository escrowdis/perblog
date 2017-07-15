---
#layout: post
title: "Scale Interval II - Histogram of pixels 尺規刻度自動運算"
date: 2013-01-29 18:16
author: escrowdis
comments: true
tags: [Programming]
---
繼上次利用DFT找尺規刻度<br>
這次找出一個新方法
就是利用**像素直方圖**來分析刻度的<span style="color: red">pixel to mm ratio</span>
STEPS
===
</span>從影像中找出尺規<br>
![sinningia_speciosa_front]({{ site.url }}/images/posts/005-02-F.jpg)
- - -
再利用erode, dilate等清晰尺規刻度
![ruler_processed]({{ site.url }}/images/posts/1313.jpg)
- - -
接著統計each rows所含的像素點即可得到<br>
![ruler_histogram]({{ site.url }}/images/posts/ruler_histogram_005-02.jpg)
- - -
接著經過回歸化去除特異值 (爆表或太低之類的值) 做平均<br>
取每個peak的最右邊或左邊 (因為每1mm的刻度在影像中並非只有1 pixel)<br>
這樣就可以找到尺規刻度拉~

測試過還不錯準<br>
平均誤差大約在**3%以內**
