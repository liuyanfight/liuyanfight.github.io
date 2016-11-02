---
layout: post
title:  "重新配置服务器中shadowsocks"
date:   2016-10-27
categories: Software
tags: Software Server
location: UTS Library
finished: true
---

Digtalocean中剩余的30多刀coupon突然说到期了，简直崩溃，本来可以用到明年8月的，还好在网上搜到可以尝试提问要回来，客服果然同意了，不过说有效期只有一年，绝对够用了，真心考虑以后每个月续租的问题，一个月5刀，30多块钱完全可以接受。不过如果在UTS的服务器回国后可以继续用就更好了。

服务器中的shadowsocks不知道为何失效了，重新配置一下。  
参考 https://shadowsocks.be/9.html


配置成功。

```
Congratulations, ShadowsocksR install completed!
Server IP:  107.170.209.4
Server Port:  8080
Password:  pwd....
Local IP:  127.0.0.1
Local Port:  1080
Protocol:  origin
obfs:  plain
Encryption Method:  aes-256-cfb
```

为防止出现上次那种网页失效，不知道以前怎么配置的尴尬事件，记录如下：

__关于本脚本：__  
一键安装 ShadowsocksR 服务端。  
请下载与之配套的客户端程序来连接。  
（以下客户端只有 Windows 客户端和 Python 版客户端可以使用 SSR 新特性，其他原版客户端只能以兼容的方式连接 SSR 服务器）

__默认配置：__  
服务器端口：自己设定（如不设定，默认为 8989）  
客户端端口：1080  
密码：自己设定（如不设定，默认为teddysun.com）  

__客户端下载：__  
[Windows](https://github.com/breakwa11/shadowsocks-csharp/releases) / [OS X](https://github.com/shadowsocks/shadowsocks-iOS/wiki/Shadowsocks-for-OSX-Help)  
[Linux](https://github.com/shadowsocks/shadowsocks-qt5)  
[Android](https://github.com/shadowsocks/shadowsocks-android) / [iOS](https://github.com/shadowsocks/shadowsocks-iOS/wiki/Help)  
[OpenWRT](https://github.com/shadowsocks/openwrt-shadowsocks)

__使用方法：__  
使用root用户登录，运行以下命令：

```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
```

__卸载方法：__  
使用 root 用户登录，运行以下命令：

```
./shadowsocksR.sh uninstall
```

安装完成后即已后台启动 ShadowsocksR ，运行：

```
/etc/init.d/shadowsocks status
```

可以查看 ShadowsocksR 进程是否已经启动。  
本脚本安装完成后，已将 ShadowsocksR 自动加入开机自启动。

__使用命令：__  
启动：/etc/init.d/shadowsocks start  
停止：/etc/init.d/shadowsocks stop  
重启：/etc/init.d/shadowsocks restart  
状态：/etc/init.d/shadowsocks status  

配置文件路径：/etc/shadowsocks.json  
日志文件路径：/var/log/shadowsocks.log  
代码安装目录：/usr/local/shadowsock

__多用户配置 sample：__

```
{
    "server":"0.0.0.0",
    "server_ipv6": "[::]",
    "local_address":"127.0.0.1",
    "local_port":1080,
    "port_password":{
            "8989":"password1",
            "8990":"password2"，
            "8991":"password3"

    },
    "timeout":300,
    "method":"aes-256-cfb",
    "protocol": "origin",
    "protocol_param": "",
    "obfs": "plain",
    "obfs_param": "",
    "redirect": "",
    "dns_ipv6": false,
    "fast_open": false,
    "workers": 1

}
```


按照这个网址 https://shadowsocks.be/6.html 安装了定时任务脚本
