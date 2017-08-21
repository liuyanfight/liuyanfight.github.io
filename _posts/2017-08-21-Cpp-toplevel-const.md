---
layout: post
title: 拷贝初始化与直接初始化
date: 2017-08-17 
categories: C++ 
tags: C++ C++Primer
location: 杭州，滨江
finished: true
---

## 声明

> `const int *p` 表示：\*p类型为 int 并且不可变；而 int \* const p 表示：\* const p属于 int，即：p 属于int \*并且不可变。

## 顶层const与底层const

- 顶层const，top-level const，表示任意的对象是个常量；
- 底层const，low-level const，表示指针所指的对象是一个常量，与基本类型部分有关。

拷贝操作，对顶层const没有什么影响，双方对象必须有相同的底层const资格。

```c++
int i = 0;  
const int ci = 42;   // 不能改变 ci 的值，这是一个顶层 const  
i = ci;   // 正确：ci 是一个顶层 const，对此操作无影响  
const int *p2 = &ci;  // 允许改变 p2 的值，这是一个底层 const  
const int *const p3 = p2;  // 靠右的 const 是顶层 const ，靠左的是底层 const  
p2 = p3;   // 正确：p2 和 p3 指向的对象的类型相同，p3 顶层 const 的部分不影响  

int *p = p3;  // 错误：p3 包括底层 const 定义，而 p 没有  
p2 = p3;   // 正确：p2 和 p3 都是底层 const 
p2 = &i;   // 正确：int* 能转换成 const int*  
int &r = ci;  // 错误：普通的 int& 不能绑定到 int 常量上  
const int &r2 = i;  // 正确：const int& 可以绑定到一个普通 int 上 
```
## Reference

[顶层const与底层const。C++的对象中的对象究竟是指？](https://www.zhihu.com/question/24785843)