---
layout: post
title: "Form BigBang to 5G 笔记"
subtitle: "有付出就要有收获 不要偷懒 "
date: 2018-1-14
location: Home
category: 通信
tags: LTE 5G 
finished: false
typora-copy-images-to: ..\img\blog\20180114
---

> 公司大牛最近每周牺牲晚上时间给大家讲5G，不认真听讲认真整理笔记的话就太浪费了。希望学有所得。
>
> PS：可以发吗？能发吗？不管了，反正没人看 :sweat_smile:。个人笔记
>
> 20180620, 第二轮了。。。啪啪啪

![img](https://pic1.zhimg.com/80/v2-e318307eecf20fb73a85112473f00b88_hd.png) 

## 序章一：物理层先验概念

### GP的概念

![1516666144348](../img/blog/20180114/1516666144348.png)

如上图case1是不可能做到的，也就是说UE发射接收机不可能同时工作在发射和接收两个频率上。但case2的情况，就是任意一个发射接收机能够做到的。而基站从下行接收到上行发送之间的间隔就是GP(Guard Period). GP的大小就是(小区半径\*2)/c（c为光速）。

__Q:从下行到上行需要GP，那么从上行到下行是否需要GP呢？__

从上行到下行，对于终端来说天然就带有一段GP所以不需要额外的GP。

> **[GP – Guard Period](http://blog.csdn.net/wo17fang/article/details/41787909)**
>
> In LTE , the radio frame structure type 2 is used for TDD operation and consists of two half-frames with a duration of 5ms each and containing each 8 slots of length 0.5ms and three special fields ( DwPTS , GP and UpPTS ) which have configurable individual lengths and a total length of 1ms. The GP is between the DwPTS and the UpPTS.

GP根据DwPTS、UpPTS长度，GP长度对应为1~10个symbol。 保证距离天线远近不同的UE上行信号在eNodeB的天线空口对齐；提供上下行转化时间 （eNodeB的上行到下行的转换实际也有一个很小转换时间Tud，小于20us），避免相邻基站 间上下行干扰 ；GP可以防止信道间干扰(ICI)。

电磁波的传送时间与距离息息相关，其损耗除了距离上的消耗还包括多径（折射）引起的时间消耗。因此，任何上行传输，都会提前至少(小区半径/c)。

在3G TDSCDMA， 4G TDD和5G的帧结构中，Gp的位置就是为了适应上行传送提前于下行传送。因此，Gp就位于DL symbol和UL symbol的转换中间，如下图。

![1516667162404](../img/blog/20180114/1516667162404.png)

频率越高的电磁波衰减越快，绕射和衍射现象越弱（越高的频率，波动性越不明显，而粒子性越明显）。方向性就越好，beam forming就有了用武之地（但会存在阴影衰弱）。

__Q:为什么频率越高，beam就越强？__



>**[为什么频率越大的光粒子性越显著？](https://zhidao.baidu.com/question/1831757384588954340.html)**
>
>这主要可以从波长的物理意义来看.
>波长越长的话,波的衍射、干涉等波所独有的现象也就越明显.因此,可以说是波动性越明显,我们越容易观察到物体的干涉、衍射这些反应波动性的现象.
>而“频率越高,粒子性越明显”,你可以从相反角度理解,频率与波长成反比,频率高了,起波长必定小,也就是说越难观察到物质的符合波动的行为,因此说粒子性越明显!
>
>**阴影衰落**是指电磁波在传播路径上受到建筑物阻挡产生的阴影效应所带来的损耗。

### 频率与波长

Ref：5G无线通信与4G的典型区别有哪些？用了哪些新技术？ - 小枣君的回答 - 知乎 https://www.zhihu.com/question/53878059/answer/196639397 

![img](https://pic3.zhimg.com/80/v2-e97629f4be22968406e6e4a3236f27ea_hd.png) 

> [波长，频率，传播距离三者的关系](https://blog.csdn.net/guomutian911/article/details/42919283)
>
> **定理：速度 =波长 * 频率；**
>
> 在光波里面,波长*频率=一个定值,所以波长越长,频率就会越小.
> 波长越长,穿透力越强(容易绕过障碍物,发生衍射),反之就弱.
> 频率越高,分辨率就越高,反之即然.
> 红外线望远镜(波长长)能在有雾的地方看得比普通的要远好多,就连窗帘布也能穿过.
> 紫外线照相机(频率高)常用于拍指纹.(用于犯罪侦破)。

5G频段分为<6GHz与>25GHz两种，对于国际上通用的28GHz来说，

![img](https://pic4.zhimg.com/80/v2-a9c1411ccc16a08c27fbd5f8c1517153_hd.png) 

即mmW毫米波。**频率越高（波长越短），就越趋近于直线传播（绕射能力越差）**

根据天线特性，天线长度应与波长成正比，大约在1/10~1/4之间。多天线阵列要求天线之间的距离保持在半个波长以上。高频率所需的天线长度更短，进而Massive MIMO就可以派上用场啦 。

### 5G中3GPP的物理帧格式

SCS(sub-carrier spacing):

