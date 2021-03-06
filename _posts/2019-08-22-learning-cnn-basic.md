---
layout:     post
title:     cnn basic learning
date:       2019-08-22
author:     Datoucai
header-img: img/turtlrtitle3.jpg
catalog: true
tags:
    - cnn
    - mxnet


---

> 龟龟是最可爱的猫

### Dense Layer/ Fully Connection Layer

全连接层本质上是特殊的卷积层，卷积层每个卷积核（kernel）的感受野是输入图像的局部区域，而全连接层相当于用了一个和原图一样大的卷积核。

- 假设输入是300\*300\*1024， 全连接层的K=4096，那么实际上相当于卷积核尺寸为**300\*300\*4096**, 也就不需要继续划窗卷积了，一次即可，一共有4096个filter，每个filter即卷积核的输出都是一个标量点。输出通道数为4096。本例中全连接层输出为**1\*1\*4096**，乘法计算量为**300\*300\*1024\*4096** ,加法计算量为4096次。参数量为**1x1x300x300x1024x4096** 。

- 仍然是这个300×300×1024的输入，假设其后接卷积层，卷积核尺寸为3\*3\*4096, 步长为1，padding为0，那么其输出特征图的尺寸为乘法计算量为**300×300×3×3×1024×4096**。（不考虑边缘的减少），参数量为 **3×3×1024x4096**

对比可见，全连接层的参数个数是卷积层的数以倍计。由于权值共享，卷积层的参数量大大减小


### Batch Normalization

### L1 Smooth


























#### 参考
1. [知乎：卷积神经网络时间复杂度分析](https://zhuanlan.zhihu.com/p/31575074)
2.[cs231n文档：convolutional-networks](http://cs231n.github.io/convolutional-networks/#fc)
