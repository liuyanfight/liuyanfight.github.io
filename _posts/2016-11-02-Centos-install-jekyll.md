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

## 给用户L,加入sudoer  

sudo的作用就是使当前非root用户在使用没有权限的命令 时，直接在命令前加入sudo，在输入自己当前用户的密码就可以完成root用户的功能，而不必在每次使用su -来回切换用户了。sudo的配置文件位于/etc/sudoers，需要root权限才可以读写。

```
vim /etc/sudoers

找到root ALL=(ALL) ALL这一行，在后面再加上一行就可以了（不用引号）：
L ALL=(ALL) ALL
其中username为指定的使用sudo的用户，引号内的空格为tab
如果你想每次使用sudo命令的时候都提示你输入根密码，移动到这一行：
#%wheel ALL=(ALL) ALL
解除#号注释
如果你不想每次使用sudo命令的时候都提示你输入跟密码，移动到下面这一行：
#%wheel ALL=(ALL)NOPASSWD:ALL
解除#号注释
保存后退出

添加用户名到wheel用户组：
usermod -G wheel username
```
user: L
pwd:pwd.

发现自己一开始就一直使用root权限，导致文件都只有root用户才可以编辑。尴尬。

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
