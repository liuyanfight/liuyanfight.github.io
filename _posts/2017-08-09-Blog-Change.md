---
layout: post
title: Blog 历史变化
subtitle: "Blog Changing ~ "
date: 2017-08-10 17:47
categories: C++ 
tags: C++ C++Primer
location: Nokia Townhall
finished: false
typora-root-url: ..
---

Blog 建立于2016/07/21，来自[Nice Blog](https://github.com/itisbenjamin/Nice_Blog).

应该是出发去悉尼前，还在实验室的时候。  
在悉尼时候用了很久，后来就荒废了。

在上面吐槽抱怨了很多，决定还是隐藏起来。

## 2016-07

添加google calendar页面，添加project页面。
添加miniblog，类似博客。

## 2017-08-10

修改Calendar页面，使用日历图片代替日历，添加记日功能。通过修改`fightingday`达到。

修改code主题，加边框，灰色背景，突出效果。修改`.highlight` 和` .highlight rouge`

增加code .highlight margin属性

无法使用emoji功能，添加后无法加载文章

## 2017-08-14
修改分割线，颜色加深，加宽

修改引用样式， border加宽加黑，改变字体

## 2017-08-17
修改archive 图标，添加未完成文章标记，修改Everyday图标

## 2017-08-18

继续在Mint系统中部署jekyll以方便修改布局而不用每次都push push push

而且要看看到底为什么emoji和task不能用

[Setting up your GitHub Pages site locally with Jekyll](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)

### ERROR：

- jekyll serve

![2017-08-18_145908](/img/blog/20170809/2017-08-18_145908.png)

​	执行`bundle exec jekyll serve`即可。

- update config file

![2017-08-18_150232](/img/blog/20170809/2017-08-18_150232.png)

​	config文件中的gems需要修改为plugins，所以之前是没有插件的原因吗？

- javascript runtime

![2017-08-18_150728](/img/blog/20170809/2017-08-18_150728.png)

```sh
sudo apt install nodejs
sudo apt install therubyracersmiley:
```

- 删除多版本jekyll

  `gem uninstall jekyll`

- emoji不能显示

  在emoji加载时不知怎么造成了注释的混乱，因此内容无法显示。完全删除该注释(google analysis)即可

  添加emoji css样式，以inline模式加载

  [emoji list](https://www.webpagefx.com/tools/emoji-cheat-sheet/)

- 还是搞不定任务列表orz :sweat:

## 2017-08-21

修改404page,显示图片

隐藏miniblog横向滚动条

emoji表情代替checkbox



