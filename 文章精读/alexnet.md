# ImageNet Classification with Deep Convolutional Neural Networks

## Introduction
做的问题关于图像识别，也就是图像分类，分类的数据集越大越好，引出了ImageNet数据集

介绍CNN的优势，有了GPU的算力，使得现在能够在ImageNet这样的数据集上应用CNN不过拟合

这篇文章的贡献有：1、做了一个很大的网络，在ImageNet数据集上效果嘎嘎好。2、做的是GPU上实现的2D卷积神经网络。3、网络包含不常见的特征来提升性能降低训练时间。4、使用了一些避免过拟合的小手段。5、最后的网络包含5个卷积层和3个全连接层，网络的深度很重要，去掉任何一层都会影响最后的准确性

在两个GTX 580 3GB的GPU上训练

## Dataset
ImageNet数据集包含的图片分辨率不一样，这篇工作的作者没有对图片进行特征提取，只是剪裁成256*256的大小，实现的是end-to-end的模式，输入的原始图片直接分类。【we trained our network on the (centered) raw RGB values of the pixels】

**简单有效的东西才持久**

## Architecture
ReLU做激活函数训练速度很快（在当时认为）
在多个GPU上做训练，把网络怎么切到两个GPU上（现在很有用，模型并行）
正则化（过时了）
对传统的Pooling进行了改动，做成了overlap的

## Reducing Overfitting
data augmentation
dropout

## Details of learning
用SGD调参数