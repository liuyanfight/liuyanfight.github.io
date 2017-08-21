---
layout: post
title: 左值引用与右值引用(ch13继续)
date: 2017-08-21
categories: C++ 
tags: C++ C++Primer
location: 杭州，滨江
finished: false
---

## 左值与右值

- 左值是可以位于赋值运算符 `=` 左侧的表达式（当然，左值也可以位于 `=` 的右侧）**非临时对象**
- 右值是不可以位于赋值运算符 `=` 左侧的表达式。**临时对象**

一个表达式是左值还是右值，取决于我们使用的是它的**值**还是它**在内存中的位置**（作为实例的身份）。也就是说一个表达式具体是左值还是右值，要根据实际在语句中的含义来确定。

1. 简单的赋值语句

```c++
int i  = 0; //i为左值， 0为右值
```

2. 右值也可以出现在赋值表达式的左边，但是不能作为赋值的对象，因为右值只在当前语句有效，赋值没有意义

```c++
((i>0) ? i : j) = 1; // 0为右值，但赋值对象i、j均为左值
```

## 左值引用和右值引用

右值引用 (Rvalue Referene) 是 C++ 新标准 (C++11, 11 代表 2011 年 ) 中引入的新特性 , 它实现了转移语义 (Move Sementics) 和精确传递 (Perfect Forwarding)。它的主要目的有两个方面：

1. 消除两个对象交互时不必要的对象拷贝，节省运算存储资源，提高效率。
2. 能够更简洁明确地定义泛型函数。


左值的声明符号为`&`， 为了和左值区分，右值的声明符号为`&&`。

## 引用的值类型与引用叠加

## 转移语义

## 引用的使用

### move 语义

### 完美转发（perfect forwarding）

### 移动迭代器（move_iterator）

## Reference

[谈谈 C++ 中的右值引用](https://liam0205.me/2016/12/11/rvalue-reference-in-Cpp/)

[从4行代码看右值引用](http://www.cnblogs.com/qicosmos/p/4283455.html)

[C++11 标准新特性: 右值引用与转移语义](https://www.ibm.com/developerworks/cn/aix/library/1307_lisl_c11/index.html)

[如何评价 C++11 的右值引用（Rvalue reference）特性？](https://www.zhihu.com/question/22111546)