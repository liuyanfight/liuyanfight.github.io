---
layout: post
title: 拷贝初始化与直接初始化
date: 2017-08-17 
categories: C++ 
tags: C++ C++Primer
location: Hangzhou, Binjiang
finished: false
---

## Reference

- [从汇编角度看c++拷贝初始化和直接初始化的底层区别](http://www.cnblogs.com/cposture/p/4925736.html)
- [C++的直接初始化与复制初始化](https://sqrt-1.me/?p=241)

## 初始化与赋值

初始化与赋值是完全不同的两个操作。

初始化的含义是在创建变量时赋予初始值，而赋值是指把对象的当前值擦除，以新值替代。

## 拷贝初始化与直接初始化

拷贝初始化 copy initialization

直接初始化 direct initialization

```c++
string s5 = "hiya"; //拷贝初始化
string s6("hiya"); // 直接初始化
string s7(10,'c'); //直接初始化
```

如上，如果使用等号`=`初始化变量，实际上执行的是拷贝初始化，编译器把右侧的初始值拷贝到新创建的对象中。当需要对多个值使用拷贝初始化时，需要显式的创建一个（临时）对象用于拷贝。

```c++
string tmp(10,'c');
string s8 = tmp;
```





