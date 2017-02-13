---
layout: post
title: RCNN->fast-RCNN->faster-RCNN
categories: [blog ]
description:
comments: true
published: true
header-img: "img/18.jpg"
tags:
     - Deep Learning
     - RCNN
---

RCNN : Region proposal + CNN

RCNN 作用是物体检测和定位



1） 通过selective search 选取region proposal（包含最终的bounding-box）

> region proposals 作者指出近几年有很多的产生region proposals的方法，而RCNN中使用的是【J. Uijlings, K. van de Sande, T. Gevers, and A. Smeulders. Selectivesearch for object recognition. IJCV, 2013.】和【X. Wang, M. Yang, S. Zhu, and Y. Lin. Regionlets for generic objectdetection. In ICCV, 2013.】中的方法。

2） region proposal  ***resize***  to 227×227

*各向异性缩放（扭曲）*

*各项同性缩放（补或不补原画面，到原画面外用平均像素补）*

3） CNN 特征提取 得到每个region proposal的feature map。

使用Alexnet，VGG16（VGG精度高，计算量大）

4） svm（二元线性）判断其物体类别还是background，每个region得到一个score

5）选取最大几个score的region，用非极大值抑制canny来进行边缘检测，得到最终的bounding-box



![相关图片](https://andrewliao11.github.io/images/faster_rcnn/rcnn_network.png)

训练过程![img](http://img.blog.csdn.net/20160308133630424?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)![img](http://img.blog.csdn.net/20160308134549350?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)![img](http://img.blog.csdn.net/20160308135140961?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

r-cnn需要两次进行跑cnn model，第一次得到classification的结果，第二次才能得到(nms+b-box regression)bounding-box。



R-CNN： 

1. 训练时要经过多个阶段，首先要提取特征微调ConvNet，再用线性SVM处理proposal，计算得到的ConvNet特征，然后进行用bounding box回归。 
2. 训练时间和空间开销大。要从每一张图像上提取大量proposal，还要从每个proposal中提取特征，并存到磁盘中。 
3. 测试时间开销大。同样是要从每个测试图像上提取大量proposal，再从每个proposal中提取特征来进行检测过程，可想而知是很慢的。





### SPP-net

SPPNet将任意大小的图像池化生成固定长度的图像表示。SPPNet放在卷积层后面。



### Fast-Rcnn 改进：

1. 比R-CNN更高的检测质量（mAP）； 
2. 把多个任务的损失函数写到一起，实现单级的训练过程； 
3. 在训练时可更新所有的层； 
4. 不需要在磁盘中存储特征。 

解决方式具体即以下几点:

1. FRCN实现了end-to-end的joint training(提proposal阶段除外)。
2. RCNN提取特征给SVM训练时候需要中间要大量的磁盘空间存放特征，FRCN去掉了SVM这一步，所有的特征都暂存在显存中，就不需要额外的磁盘空间了。
3. 然后FRCN进一步通过single scale(pooling->spp just for one scale) testing和SVD(降维)分解全连接来提速。

![img](http://img.blog.csdn.net/20150804155941418)



ROI pooling layer 规整大小

Multi-task loss

Scale invariance



### faster-RCNN

![这里写图片描述](http://img.blog.csdn.net/20160414164536029)

Region Proposal Networks 把区域选择方法融合进网络，用GPU加速。



### YOLO

![这里写图片描述](http://img.blog.csdn.net/20160317163739691)

分成SxS个网格（grid cell）

每个网格预测B个bounding box，每个bounding box带一个confidence值，

这个confidence代表了所预测的box中含有object的置信度和这个box预测的有多准两重信息。

每个网格还要预测所属类别。

使用VGG-16



### YOLO9000

***better，faster，stronger***

使用GoogLeNet，更快

Batch Normalization （批量规范化）

High resolution classifier 高分辨率

提出WordNet，而非传统的Softmax分类。
