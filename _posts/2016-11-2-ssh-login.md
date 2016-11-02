---
layout: post
title:  "配置服务器中用户"
date:   2016-11-02
categories: Software
tags: Software Server
location: UTS Library
finished: true
---

> 发现自己在服务器中一直以root用户运行，这样不好~~

## 创建用户 L  

```
useradd L
passwd L
...
pwd...

```

发现已经有了...

## ssh密钥登录（用户L）

在服务器端使用用户L登录，在其~目录下  

使用 `ssh-keygen -t rsa` 生成密钥对，保存在.ssh文件夹下

复制公钥到authorized_keys
`cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys` 

更改权限（不改登不上。。）  
`chmod 400 ~/.ssh/authorized_keys`

至此，服务器端配置结束。下面在windows端配置。

复制私钥id_rsa到本地，使用puttygen导入后，保存私钥`rsa-key-20161102-4-centos-L`。

至此，就可以使用保存后的私钥登录服务器了。

好好奇以前自己怎么配置的，已经完全没有印象了。。 

:happy
