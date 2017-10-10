---
title: 重温统计学习基础 1 (overview of superivsed learning)
author: Wang Tuo
toc: true
date: 2017-07-23 15:11:08
tags:
- base
- theory    
categories: ml
mathjax: true
description: 本文主要内容：比较了监督学习中两种最基础的模型，探讨了如何才能求得真实函数$f(x)$的近似。
---

重新温习统计学习基础一书，整理心得体会和重要知识点。

## 绪论
### 提问：
- [x] 最小二乘和最近邻有什么不同假设？
  一个是假定真实模型可以用全局线性函数近似，一个假定真实模型可以用局部常量函数近似
- [x] 有哪些在最小二乘和最近邻间平衡的模型？
  光滑样条算不算？还有局部回归
- [x] 有哪些对最小二乘估计线性模型于最近邻法的拓展？
  核方法，依据距离对点加权的k近邻；局部回归（局部加权最小二乘）；基展开


### 两种基本的预测方法：最小二乘和最近邻
使用最小二乘估计的线性模型做了大量假设，可以得到稳定但有可能精确度相对较低的预测结果，最近邻方法假设很少，可以得到精确但不稳定的预测结果。（这两种方法之间的选择就是典型的方差偏差权衡，也有折中的做法如光滑样条）
最小二乘：
$$RSS(\beta)=(y-\mathbf{X}\beta )^{T}(y-\mathbf{X}\beta )$$
$$\frac{d(RSS(\beta))}{d(\beta)}=\frac{d((y-\mathbf{X}\beta )^{T}(y-\mathbf{X}\beta ))}{d(y-\mathbf{X}\beta )}\frac{d(y-\mathbf{X}\beta )}{d(\beta)}$$
$$\frac{d(RSS(\beta))}{d(\beta)}=2(y-\mathbf{X}\beta)*(-\mathbf{X}^T)$$
注意：$\frac{d(A\mathbf{X})}{d(\mathbf{X})}=A^T \mathbf{X}$
则有，如果$\mathbf{X}^T \mathbf{X}$可逆，则有$\widehat{\beta }=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^Ty$

### 统计决策理论
给定损失函数，求使期望损失函数最小的$f$
对k近邻而言，实质上是求$f(x)=E(Y|X=x)$，这里做了两次近似，1.以平均作为期望的近似；2.在点上取条件期望放宽为在靠近目标点附近的区域上取条件期望。有两个主要问题影响k近邻的性能，1是稳定性，2是样本稀疏
对最小二乘拟合的线性模型而言，是用一个全局线性函数来近似$f(x)$





