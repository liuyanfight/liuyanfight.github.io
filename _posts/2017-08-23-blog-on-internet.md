---
layout: post
title: Github Page添加Google收录等相关服务
date: 2017-08-23
categories: Tool
tags: Tool Software
location: Nokia Townhall
finished: true
---

> 想了一下还是google收录一下blog，不然就太无聊了，看到点击与评论也是一种鼓励，很有成就感的。

## Google Analytics

忘记怎么创建的了。。。大概就是申请账号吧:yum:

## Google收录

用自己的google帐号登陆 [Webmaster Central](https://www.google.com/webmasters/tools/home?hl=zh-CN)，添加站点并验证。

有多种验证方式，添加html文件算是比较方便的。

将验证文件放到 repo下

push后尝试访问添加的页面，成功即可

## 添加sitemap

提交站点地图文件有助于Google 更好地决定如何抓取您的网站。

在config.yml中添加plugins`jekyll-sitemap`

将 http://liuyanfight.github.io/sitemap.xml 添加到google search console的站点地图中

