# 行为识别

**目标**

给视频片段进行一定的分类，类别通常是各类人的动作

**特点**

一个视频片段中包含一段明确的动作，所以也可以看作是输入为视频，输出为动作标签的多分类问题。

**难点**

特征：即如何在视频中提取出能更好的描述视频判断的特征。特征提取的越好，则分类的效果越好。

特征的编码（encode）/融合（fusion）：这一部分包括两个方面：

空间方面的，在使用多种特征的时候如何编码/融合这些特征以获得更好的效果；

时序方面的，视频很重要的一个特性就是其时序信息，一些动作看单帧的图像是无法判断的，只有通过时序上的变化判断，所以需要将时序上的特征进行编码或者融合，获得整个视频的特征描述。

算法速度：在训练的时候，算法的速度不是特别重要。但是产品上线需要快速的算法。

**研究进展**

非深度学习方法：Action recognition with improved trajectories 

IDT（improved dense trajectories）算法稳定性不错，速度比较慢。基本思路，利用光流场来获得视频中的轨迹。沿着轨迹提取，HOF,HOG,MBH,trajectory等特征。

HOF基于灰度

其他基于dense optical flow\(密集光流\)，最后用Fisher Vector特征编码，基于结果训练SVM分类器。iDT改进的是利用前后两帧的光流以及SURF关键点进行匹配，可以用来消除/减弱相机运动带来的影响。

![](/assets/import.png)





**深度学习方法**

Two Stream Network系列

[Two-Stream Convolutional Networks for Action Recognition in Videos （2014NIPS）](https://arxiv.org/pdf/1406.2199.pdf)

主要分为

本文采用学习大量融合Convent的既有tower是spatially空间的 还有patio-temporal 时间的.我们达成了如下的发现：

与softmax层融合相比,一个时空网络层可以融合但是不失性能.最后一层融合比较好.池化抽象卷积在相邻时空的特征会提升性能。



