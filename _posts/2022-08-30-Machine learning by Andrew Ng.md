---
layout: post
title:  "Machine learning by Andrew Ng"
date:   2022-08-30 10:29:00 +0800
categories: Machine learning
---

> 最近在看Andrew Ng的机器学习视频，因此记录一下学习笔记。对于本课程我总结了几个比较关键的点， 他们分别是逻辑回归、正则化、梯度下降、反向传播、SVM和PCA。

# 逻辑回归(Logistic Regression)

其实本质上，我觉得和线性回归是一致的，套用了一个激活函数。形式上大概就是 **sigmoid(线性回归)=逻辑回归**。因为借助了sigmoid的映射关系，可以对数据降敏，排除极端值的影响，对结果定性。但是受限于使用场景，**非线形分布**的事务决策结果也不理想。

二分类和多分类：

![sigmoid](/images/sigmoid.jpg)



# 梯度下降

梯度下降，首先究其本质，梯度下降本身离不开损失函数，损失函数就是样本初始值经过模型预测得到一个预测值，预测值和真实值之间的差距就是损失函数，究其本质就是**计算预测值和真实值差距的一类函数泛指**，例举L1Loss和CrossEntropyLoss

![loss](/images/loss.jpg)





 CrossEntropyLoss被应用于逻辑回归中，同上一节。

![image-20220909165904163](/images/image-20220909165904163.png)



很多对梯度下降的解说都会用山谷来形容，通过一个加速度和方向（二维的话，方向单一，所以不做考虑），让小球在一个空间内（一般是三维）移动，触及最低点



<div align="center">    <img src="https://ruder.io/content/images/2016/09/contours_evaluation_optimizers.gif"  height=400><img src="https://ruder.io/content/images/2016/09/saddle_point_evaluation_optimizers.gif" height=400> </div>

贴两张经典动图，当然这里是放了一些optimizer的比较，但是从这个轨迹可以窥见梯度下降的过程。

## Gradient Descent Optimization

梯度下降的优化集中在学习率和加速度上，根据我之前学习的映像，本质都是要解决**加速度过小冲到山谷耗时长**、**加速度过小冲不出局部最优解**和**加速度过大始终没法定位到山谷**的三个核心点。主要的几个算法如下。课程里面没有怎么讲这部分，这部分内容开一个新blog写。

![image-20220909173650070](/images/image-20220909173650070.png)



# 正则化

![20220913](/images/20220913.jpg)

正则化在Andrew课程里面讲的不深，正则化的出现，是因为过拟合的问题。**在早期用多项式函数去拟合训练样本的时候，多分的贴合训练数据会导致loss function趋近于0，这会导致拟合曲线没有泛用性**，因此我们设置一些去敏的策略：

1. 缩减变量的个数：舍弃一些变量，保留更为重要的信息，但是基于这种策略下，势必会造成一些信息的缺失。
2. 正则化：**保留所有的变量，将一些不重要的特征的权值置为0或权值变小使得特征的参数矩阵变得稀疏，使每一个变量都对预测产生一点影响。**

关于正则化，我参考了[正则化(regularization)总结](https://zhuanlan.zhihu.com/p/128129015)以及[L1、L2正则化总结](https://blog.csdn.net/Yasin0/article/details/89682616)，常见的正则化方法有lasso回归（l1），岭回归（l2）。

![](/images/regression.jpg)



通过添加正则项，可以使模型的部分参数值都较小甚至趋于0，对应的特征对模型的影响就比较小，相当于对无关特征做了一个惩罚，即使它们的值波动比较大，受限于参数值很小，也不会对模型的输出结果造成太大影响。简而言之，**正则化是将模型参数加入到损失函数中，能避免权值过大，模型过于陡峭**，从而降低过拟合。


<div align=center><img src="https://img-blog.csdnimg.cn/2019070323172473.png"></div>

关于l1和l2的比较，一般常见的是对解空间进行对比。如上图所示，

# 反向传播

![20181105140730857](../images/20181105140730857.jpg)

关于backpropogation 我认为目前就是这几个算法中的核心算法，也是损失函数能对神经网络起作用的本质原因。我例举了上述的优化方程，来梳理一下backforward的优化原理



# SVM

# PCA
