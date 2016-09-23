---
layout: post
title: "Andrew Ng 的 机器学习课程"
subtitle: "Again"
date: 2016-09-20 18：37
author: L
category: Machine Learning
tags: 学习 ML
finished: true
---

> 上一次学习这个课程是在2014-08-15左右，刚研究生的时候，现在我已经快要研究生毕业了，说实话，这两年除了年纪长了之外没有什么长进，想想也是可悲。上一次没有坚持到最后，这次要加油。

> 现在学习课程材料真的超级齐全。

## Introduce
### What is Machine Learning?

__Machine Learning__ 的定义：

  - Arthur Samuel：Field of study that give computers the ability to learn without being explicity programed.
  - Mitchell ：A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E.

机器学习可以视为解决两个问题

  - supervised learning,
  - unsupervised learning.

课程涉及讨论的算法：   

  - Supervised learning 监督学习
  - Unsupervised learning 非监督学习
  - Others: Reinforcement learning, recommender  systems
  - Also talks about: Practral advice for applying learning algorithm.

### Supervised learning

监督性学习就是使用带有标签的数据集来学习。监督性学习问题可以被分为 "regression"（回归） 和 "classification"（分类）两种。

回归问题是指预测的结果是连续的输出。分类问题预测的结果是不连续的。

### Unsupervised Learning

非监督性学习是指不知道结果的情况下探索数据的结构性质或是相似性（即不包含label信息）。非监督性学习问题严格上说没有结果来比较。比如聚类问题。

$$\hat{y} = h_\theta(x) = \theta_0 + \theta_1 x$$

Linear Regression with one Variable
  介绍一个变量的线性回归算法，介绍了梯度下降算法来计算theta。

3. Multiple features (variables)
        多个变量的情况，介绍Gradient descent 中的 Feature Scaling, Learning rate

4. Normal equation
        Method to solve for theta analytically.

5. 比较 Gradient Descent 和 Normal Equation ，

6. 介绍Octave基本功能

7. vectorized implementation



Programming Exercises 1

2 Linear regression with one variable
2.2 Gradient Descent
2.2.3 Computing the cost J(θ)
[html] view plain copy
J = (1 / (2 * m)) * sum(((X * theta - y).^2));  
2.2.4 Gradient descent
[plain] view plain copy
% 1st  
theta = theta - alpha * ( 1 / m) * (X' * (X * theta - y));  
% 2nd  
%temp1 = theta(1) - alpha * ( 1 / m) * sum(X * theta - y);  
%temp2 = theta(2) - alpha * ( 1 / m) * sum((X(:,2) .* (X * theta - y)));  
%theta = [temp1;temp2];  
3 Linear regression with multiple variables
3.1 Feature Normalization
[plain] view plain copy
mu = mean(X);  

sigma = std(X);  

% problem: need for many other case  
[m n] = size(X);  
for i = 1:n  
    X_norm(:,i) = (X(:,i) - mu(i)) / sigma(i);  
end  
3.2 Gradient Descent
[plain] view plain copy
J = (1 / (2 * m)) * sum(((X * theta - y).^2));  

[plain] view plain copy
theta = theta - alpha * ( 1 / m) * (X' * (X * theta - y));  
3.3 Normal Equations
[plain] view plain copy
theta = pinv(X' * X) * X' * y;  
