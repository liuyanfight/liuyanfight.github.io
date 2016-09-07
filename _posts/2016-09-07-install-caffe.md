---
layout: post
title: "Caffe安装"
subtitle: "Computer Vision Software"
date: 2016-09-07 15：43
author: L
category: Computer Vision
tags: ML 学习 CV DL Sydney Software UTS
finished: true
---

> 按照要求安装了X2Go Client，相当于VPS一样的，系统是 	Ubuntu 14.04.1 LTS.
但是没有安装Caffe，需要在没有sudo权限的情况下安装。昨天测试了一晚上，没有成功，今天继续。

## Install
- Open a terminal, and download caffe
`git clone https://github.com/BVLC/caffe.git`
- make a copy of Makefile.config.example using file name "Makefile.config"
  `cp Makefile.config.example Makefile.config`
- Edit the Makefile.config file and make the following modification:
  `Uncomment USE_CUDNN := 1 to build with cuDNN`
- Change the CUDA_DIR using:
  `CUDA_DIR := /usr/local/cuda-7.5`
- Set LD_LIBRARY_PATH by editing  ~/.bashrc
  `vim ~/.basr_rc` 此处也可使用gedit
- append  `export LD_LIBRARY_PATH=/opt/lib：/usr/local/cuda-7.5/lib64`  and `export PYTHONPATH=/home/yanliu/caffe/python` to this file.
- `source ~/.bashrc`完成编译
- Then begin to build the caffe :
  `Make all -j8`
  `make pycaffe`
- Also, check out the examples in Caffe website: http://caffe.berkeleyvision.org

## Finished at 2016/09/07/16:05
