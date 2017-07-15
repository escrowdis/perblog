---
#layout: post
title: "[Qt creator] Image | Label load, resize and show Image 載入、調整大小、顯示影像"
date: 2013-02-14 05:16
author: escrowdis
comments: true
tags: [creator, image, label, Programming, Qt, Qt creator, resize, show, WordPress]
---
嗨~
Hi!
我習慣用Label來顯示圖片，<br>
I'm used to using 'label' to display image<br>
但圖片太大或太小塞不進介面時，就會用上這個了！<br>
you'll need this when you found that image size isn't fit the label size.

Solution 1
===
```c++
QString file = QFileDialog::getOpenFileName();
if(file.isEmpty())
return;
Mat image = imread(file.toStdString());
Size size;
size.width = w;
size.height = h;
cv::resize(image,image,size);
QImage img = QImage((uchar*)(image.data), image.cols, image.rows,
    QImage::Format_RGB888);
setPixmap(QPixmap::fromImage(img));
```
- - -
```c++
QString file = QFileDialog::getOpenFileName();
if(file.isEmpty()){
QMessageBox::information(., "", "No file has been loaded!");
return;
}
Mat image = imread(file.toStdString());
//這邊使用QFileDialog的openfile if那邊是如果影像沒有載入不會crash
//We use 'QFileDialog' to load the image and return if there's no image loaded
Size size;
size.width = w;
size.height = h;
cv::resize(image,image,size);
//cv::resize調整影像大小，size來訂範圍 一般來說整數比較不會有影像錯亂的現象
//cv::resize to adjust image size, usually,
// the size maybe integer to avoid image tilt by some number problem.
QImage img = QImage((uchar*)(image.data), image.cols, image.rows,
    QImage::Format_RGB888);
ui->label->setPixmap(QPixmap::fromImage(img));
//QImage 載入image 即可顯示在label囉！
```

Solution 2
===
如果只想輸出label 不想將image作放大縮小的調整 => 如果要再放大，解析度會變差
可以使用<br>
If you only want to output label without changing image size,
you can use the code below.<br>

```c++
QString file = QFileDialog::getOpenFileName();
if(file.isEmpty())
return;
Mat image = imread(file.toStdString());
QImage img = QImage((uchar*)(image.data), image.cols, image.rows,
    QImage::Format_RGB888);
QImage img_s = img.scaled(ui->label_9->width(), ui->label_9->height(),
    Qt::KeepAspectRatio);
setPixmap(QPixmap::fromImage(img_s));
```
