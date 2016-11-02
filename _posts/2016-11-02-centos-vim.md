---
layout: post
title:  "Centos安装VIM"
date:   2016-11-2
categories: Software
tags: Software Server
location: UTS Library
finished: true
---

## update Centos

centos升级系统  
`yum -y update`

## 安装字体库 & 中文字体

参考 [ Linux CentOS 7 安装字体库 & 中文字体 ](http://blog.csdn.net/wlwlwlwl015/article/details/51482065)

还不知道怎样在vim中显示chinese。。。 [微笑脸]

## 安装vim

在user L 下安装vim

[超强vim配置文件](https://github.com/ma6174/vim)

自动安装  
` wget -qO- https://raw.github.com/ma6174/vim/master/setup.sh | sh -x`

Tips:

    1. 400多种主题，在[color](https://github.com/ma6174/vim/tree/master/colors)目录下。  
    在~/.vimrc，修改`color ron     " 设置背景主题`
    2. 打开vim时不加文件名自动打开NERDTree, 关闭文件时没有其他文件自动退出NERDTree
    3. 按`F6`可以格式化C/C++/python/perl/java/jsp/xml/代码
    4. 按`F5`可以直接编译并执行C、C++、java代码以及执行shell脚本，按`F8`可进行C、C++代码的调试
    5. 自动插入文件头 ，新建C、C++源文件时自动插入表头：包括文件名、作者、联系方式、建立时间等，可根据需求在.vimrc中自行更改
    6. 映射`Ctrl + A`为全选并复制快捷键，方便复制代码
    7. 按`F2`可以直接消除代码中的空行
    8. `F3`可列出当前目录文件，打开树状文件目录 __(好用!!)__
    9. 支持鼠标选择、方向键移动
    10. 代码高亮，自动缩进，显示行号，显示状态行
    11. 按`Ctrl + P`可自动补全,[]、{}、()、""、' '等都自动补全
    12. Tab键的宽度为4
    13. 多窗口操作，使用`:sp + 文件名`可以水平分割窗口,`:vs + 文件名`可以垂直分割窗口, 使用`Ctrl + w`可以快速在窗口间切换
