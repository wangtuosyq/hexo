---
title: 周志华机器学习 心得体会（第一章、第二章）
author: Wang Tuo
toc: true
date: 2017-07-20 15:11:08
tags:
- base
- theory    
categories: ml
mathjax: true
description: 本文主要内容：机器学习的一些基本概念，以及模型评估与选择的一些常用的指标介绍
---
## 绪论
### 提问：
- [x] 泛化能力如何评价
  通过测试误差作为泛化误差的近似，留出法(hold-out),k折交叉验证(k-fold cross validation),留一法(Leave-One-Out,LOO),自助法(bootstrapping)获得测试误差
- [ ] 有哪些技术手段可以提升泛化性能 
- [ ] 哪些模型拥有相对而言更好的泛化性能
- [x] 模型训练还有哪些目标
  如时间开销，储存开销，可解释性等。
- [ ] 提升泛化性能会对这些目标造成怎样的影响
- [ ] 如何在泛化性能与这些目标之间进行trade off
- [ ] 常见的模型各自的归纳偏好是什么？适用于什么情形和数据？

### 基本概念
示例(instance)/样本(sample)/特征向量(feature vector),属性(attribute)/特征(feature),属性空间(attribute space)/样本空间(sample space),
学习(learning)/训练(training),假设(hypothesis),真相(ground-truth)
学习过程就是根据训练数据调整假设逼近真相
标签(lable),样例(example,有标签的示例)
机器学习的目标是使学得的模型能很好的适用于"新样本(unseen instance)"，即拥有良好的泛化能力
特征空间(hypothesis),与训练集一致的假设集合：版本空间(version space),对版本空间中的假设进行选择，将根据模型的归纳偏好(inductive bias)

发展历程：推理期>知识期>归纳期>归纳逻辑程序设计>连接主义学习>统计学习>深度学习

## 模型评估与选择
### 基本概念
错误率(error rate),精度(accuracy,1-error rate),误差(error),训练误差(training error)/经验误差(empirical error),泛化误差(generalizaton error),过拟合(overfitting,把训练样本自身的特点当作所有潜在样本的一般性质，导致泛化性能下降),欠拟合(underfitting,对训练样本的一般性质尚未学好),调参(parameter tuning)

### 性能度量(performance measure):
给定样例集 $D$ ,评估学习器 $f$ 的性能：
均方误差(mean squared error): $E(f;D)=\frac1m \sum\_{i=1}^m(f(x\_i)-y\_i)^2$
错误率:$E(f;D)=\frac1m \sum\_{i=1}^m\mathbb {I}(f(x\_i)\neq y\_i)$
精度：$acc(f;D)=1-E(f;D)$
对数据分布$\mathscr D$和概率密度函数$p(·)$:
均方误差：$E(f;\mathscr D)=\int\_{\mathscr D}(f(x\_i)-y\_i)^2p(x)dx$
错误率:$E(f;D)=\int\_{\mathscr D}\mathbb {I}(f(x\_i)\neq y\_i)p(x)dx$
精度：$acc(f;D)=1-E(f;D)$
对分类问题：
查准率(precision,判断为正的有多少真的是正),查全率(recall，真的是正的有多少被判断为正)
平衡点(Break-Even Point,查准率等于查全率的点)
F1度量(查准率与查全率的调和平均数)：$F1=\frac{2\times P\times R}{P+R}=\frac{2\times TP}{N+TP-TN}$
ROC(Receicer Operating Characteristic)：纵轴为真正例率(TPR=TP/(TP+FN)),横轴为假正例率(FPR=FP/(TN+FP))
AUC,ROC的面积，等于1-排序损失。
注意，对非均等代价情况下需要调整ROC的计算方式
**对多个算法，多次测试时的性能比较，可以通过假设检验来判断算法性能是否存在显著差异**

**期望泛化误差可分解为偏差，方差，噪声之和，偏差度量了学习算法的期望预测与真实结果的偏离程度，代表学习算法本身的拟合能力，方差代表了同样大小的训练集的变动导致的学习性能的变化，即刻画了数据扰动所造成的影响，噪声表达了在当前任务上任何学习算法所能达到的期望泛化误差的下界，即刻画了学习问题本身的难度**




