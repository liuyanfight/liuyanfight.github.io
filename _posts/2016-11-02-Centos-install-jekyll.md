---
layout: post
title: Centos7安装Jekyll
date: 2016-11-02 18:57
categories: Software 
tags: Software Centos Server
location: UTS Library
finished: true
---

> 在服务器上安装Jekyll，可真是太不容易了！！！我已经折腾一下午+一晚上了！看别人安装的都很简单，到自己就各种各样的错误

## 安装jekyll

安装各种依赖  
`yum install ruby ruby-devel nodejs -y`

可是！ruby一直安装不成功！中间尝试了很多，然后发现要用到rvm  
`yum instll ruby`  
一直提示：`The requested url does not exist(22): 'https://cache.ruby-lang.org/pub/ruby/./ruby-2.0.0p598.tar.bz2'`   
我他喵的简直服气了，尝试各种版本都不行，后来使用
`sudo chmod 777 -R /path/to/rvm `  
但是一般情况最好不要把775权限乱用。

你以为OK了？错。。。

`rvm install ruby`  
错误信息: `Error running __rvm_make -j1`等等  
终于！在 https://ruby-china.org/topics/15891 发现有效信息！可能是内存不够！交换文件来解决。  

 ```
 sudo mkdir -p /var/cache/swap/
 sudo dd if=/dev/zero of=/var/cache/swap/swap0 bs=1M count=512
 sudo chmod 0600 /var/cache/swap/swap0
 sudo mkswap /var/cache/swap/swap0 
 sudo swapon /var/cache/swap/swap0
 ```

终于成功了。[喜极而泣的我]



`rvm list` 可以看到安装的ruby 2.3.1，开心~

接下来就`gem install jekyll`Jekyll就安装成功拉~~

## 配置github.io

参考 https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/#step-2-install-jekyll-using-bundler

检查ruby的版本（要2.0.0以上）  
`ruby --version`

安装bundler `gem install bundler`

在github.io文件夹下创建Gemfile文件，写入  

 ```
 source 'https://rubygems.org'
 gem 'github-pages', group: :jekyll_plugins
 ```

Install Jekyll and other dependencies from the GitHub Pages gem:  
`bundle install`

Run your Jekyll site locally:  
`bundle exec jekyll serve`

Preview your local Jekyll site in your web browser at http://localhost:4000

Keeping your site up to date with the GitHub Pages gem
`bundle update`
