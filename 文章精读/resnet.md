# Deep Residual Learning for Image Recognition
2015年微软亚洲研究院提出的ResNet

使用**残差学习框架**能够比之前更容易的训练很深的神经网络

## Introduction
CNN对图片分类效果很好。

好的网络只是简单的把隐藏层堆在一起就可以了嘛？网络很深的时候会很容易出现梯度爆炸或者梯度消失。较好的初始化参数，或者层之间用normalization控制，能很大程度的解决梯度爆炸/消失的问题。这样可以训练或收敛很多很深的网络。

观察到的现象是层数越多，不管是训练误差还是测试误差都变大了（这不是过拟合）。

按道理来说，在一个层数较浅的网络里能够得到好的结果，在这个基础上后面加的那些层，如果只是identity mapping（理解成一一对应吧）的关系的话，应该不会让精度变差。然而SGD找不到identity mapping。

于是它们提出了deep residual learning framework。

假设较浅层输出的是x，常规网络后续学的内容是H(x)。而他们这帮人提出的residual学的内容是F(x)，而F(x) = H(x) - x，等F(x)学完，用shortcut connection思想再把前面的x加到F(x)。人为做一个显示的identity mapping。

这样做的好处是不会增加任何的参数，计算复杂度也不会变高，只是最后做了加法。

大量的实验表明deep residual net非常容易优化，越深精度越高。

## Related work

### Residual representations
机器学习用的很多。

### Shortcut connections
ResNet不是第一个提出来的，但是很巧妙的应用了。

## Deep residual learning
更加详细地介绍了residual learning和用shortcut做identity mapping

### Network architectures
残差连接处理输入和输出形状不同的方案。

第一个是说填充0来增加维度。

第二个是用1*1的卷积投影（因为还没看CNN这里不太明白）

还有一个bottleneck的处理技巧

### Implementation
The image is resized with its shorter side randomly sampled in [256, 480] for scale augmentation [41]. 
A 224×224 crop is randomly sampled from an image or its horizontal flip, with the per-pixel mean subtracted [21].
The standard color augmentation in [21] is used. 
We adopt batch normalization (BN) [16] right after each convolution and before activation, following [16]. 
We initialize the weights as in [13] and train all plain/residual nets from scratch. 
We use SGD with a mini-batch size of 256. The learning rate starts from 0.1 and is divided by 10 when the error plateaus, and the models are trained for up to 60 × 104 iterations. 
We use a weight decay of 0.0001 and a momentum of 0.9. We do not use dropout [14], following the practice in [16].

In testing, for comparison studies we adopt the standard 10-crop testing [21]. 
For best results, we adopt the fully- convolutional form as in [41, 13], and average the scores at multiple scales (images are resized such that the shorter side is in {224, 256, 384, 480, 640}).

## Reference
https://arxiv.org/pdf/1512.03385