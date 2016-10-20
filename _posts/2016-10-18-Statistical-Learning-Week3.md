---
layout: post
title: "Statistical learning Week 3 线性回归"
date: 2016-10-18
author: Liu
category: Statistical Learning
tags: UTS Sydney ML SL
location: UTS Library
finished: false
---

Week 3 线性回归
------

## Outline

> 线性回归模型
>   
>  - 最小二乘 Least Squares Fit
>  - 统计量 Mesures of Fit
>  - 假设检验
>
> 回归模型中的其他注意事项
>
>  - Qualitative Predictors 定性预测
>  - Interaction Terms
>
> Potential Fit Problems  
> 线性回归与KNN回归

## 线性回归模型

$$
Y_i=\beta _0+\beta _1X_1+...+\beta _pX_p+\epsilon
$$
其中，$\beta _0$代表截距，$\beta _i$代表变量$X_i$的斜率，$\epsilon$代表均值为0的随机误差项。

可使用梯度下降或牛顿迭代法来求参数$\beta$。

### 最小二乘估计 (least squares fit)

使用最小二乘法估计参数
$$
MSE=\frac 1n\sum _{i=1}^n(Y_i-\hat Y_i)^2=\frac 1n\sum _{i=1}^n(Y_i-\hat \beta _0-\hat \beta _1X_1-...-\hat \beta _pX_p)^2
$$

### 统计量(Mesures of Fit)

标准差(standard erro, SE)
$$
Var(\hat \mu)=SE(\hat \mu)^2=\frac {\sigma ^2}{n}
$$
其中 $\sigma$是变量$Y$的每个预测值$y_i$的标准差。$\sigma = \sqrt{\frac 1N \sum _{i=1}^N(x_i-\mu)^2}$,$\mu$为平均值。


残差平方和(residual sum of squares, RSS)
$$
RSS=\sum _{i=1}^n(y_i-\hat y_i)^2
$$

总平方和(total sum of squares, TSS)测量y的总方差。
$$
TSS=\sum (y_i-\overline y)^2
$$

判断线性回归的拟合质量通常使用两个相关的量：残差标准误(residual standard error, RSE)和 $R^2$统计量。

RSE是对$\epsilon$的标准偏差的估计。$R^2$统计量采用比例的方式(被解释方差的比例)。
$$
R^2=\frac {TSS-RSS}{TSS}=1-\frac {RSS}{TSS}\approx 1-\frac {Ending Variance}{Starting Variance}
$$
$R^2$统计量总是在0到1之间，0意味着模型没有解释任何variance，1意味着完美解释。

> 2016/10/19

### 假设检验 hypothesis test

在进行多元线性回归时，有一些重要问题需要解释：

1. $\beta _j$是否等于0？我们可以使用假设检验来回答。如果我们不能确定 $\beta _0 \neq j$,那么$X _j$在预测中就不存在。

2. 我们能确定至少有一个变量X是有用的吗？即$\beta _1=\beta _2=\beta _j=0$?

_$\beta _j = 0$?X是一个重要的变量吗？_

我们使用 __假设检验__ 来回答这个问题。  
检验零假设：
$$
H_0:\beta _j=0
$$

对应的备择假设是
$$
H_a:\beta _j \neq 0
$$

计算t-test，测量$\beta _j$偏离0的标准偏差。其中
$$
t=\frac {\hat \beta _j}{SE(\hat \beta _j)}
$$
当$n>30$时，t近似正态分布。假设$\beta _j = 0$，计算任意观测值大于等于$|t|$的概率，就是 __p值__ (p value)。可以认为，当p很小时，预测变量和响应变量间存在关联。

如果t比较大（p比较小），我们就可以确定$\beta _j \neq 0$，并且存在着关系。

__整个回归公式解释所有情况吗？__

假设
$$
H_0:所有的都为0，即\beta _1=\beta _2=\beta _j=0, H_a:至少一个不为0
$$

使用F检测(F test)
$$
F= \frac {(TSS-RSS)/p}{RSS/(n-p-1)}
$$
若$H_0$为真，则F统计量应该接近1，如果$H_a$为真，那么F大于1.

## 回归模型中的其他注意事项

### 定性预测变量

上面讲的都是定量(quantitative)的，也可使用回归处理分类问题。
![定性问题](/img/blog/20161014/4.png)

## K近邻回归 KNN Regression

与KNN分类近似。根据给定的X选择K个最接近的点，用这些点的平均值来估计$f(x_0)$
$$
f(x)=\frac 1K \sum _{x_i \in N_i}y_i
$$
当真实关系为非线性时，KNN比线性回归更好。

>  这一章有点乱





