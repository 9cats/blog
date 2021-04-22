---
abbrlink: '0'
title: 搭建个人博客
date: '2021/4/17 2:28:00'
updated: '2021/4/17 2:28:00'
tags: 
    - 前端
    - 后端
    - nodejs
    - npm
    - IP
    - VPS
    - linux
    - git
categories:
    - 知识分享
keywords:
description:
top_img: false
comments:
cover:
toc: 
toc_number:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
aplayer:
highlight_shrink:
aside:
---

# 1.总览

## 1.1 简介

因为我当初加入比特后不精学，对前端的兴趣一般，
而且不知道该去认真学些什么、怎么学，经过近两年的摸爬滚打，
此时的我已经是大杂烩的模样。
因此，本次分享会介绍为大家点明**学习的路线**，了解将来极可能要接触到的方方面面，以及激发一些**兴趣**。
本章会把我在比特两年中 ~~(的黑历史)~~ 学到的知识 (毕生所学) 通过搭建个人博客的搭建并部署分享出来

## 1.2 本章主要流程

搭建博客开发环境 ----> 初步尝试博客开发 ----> 将博客部署到云服务器中

## 1.3 提前准备

+ [Hexo](https://hexo.io/zh-cn/)是一款基于 Node.js 用于快速搭建博客的框架，有了它就可以完成完成个人博客的构建，它会帮你构建博客的整个框架，你只需要会使用Markdown 写博客即可。
+ [Butterfly](https://butterfly.js.org/)Butterfly 博客主题。A Simple and Card UI Design theme for Hexo.
+ [Node.js](http://nodejs.cn/) 是一个基于Chrome V8引擎的JavaScript运行环境。安装好node.js后利用npm包管理工具来安装Hexo
+ [Git](https://git-scm.com)是目前世界上最先进的分布式版本控制系统（没有之一）。对项目的备份，部署等等都大有用处。
+ [linux](https://www.runoob.com/linux/linux-tutorial.html)是一种自由和开放源码的类 UNIX 操作系统。能支持POSIX的多用户、多任务、支持多线程和多CPU，一般服务器就是都是linux。
+ [Centos](https://baike.baidu.com/item/CentOS/498948?fr=aladdin)是Linux发行版之一，还有如Debin Ubuntu等版本的linux系统可供选择。


## 1.3 涉及内容参考资料

+ <font color="red">搜索</font>
    + [谷歌](https://google.com)<font color="red">(推荐)</font>
        + [谷歌镜像](https://siguso.com/google/)
    + [百度](https://baidu.com)
+ <font color="purple">百科</font> ———— 了解新事物的最快途径
    + [百度百科](https://baike.baidu.com/)
    + [维基百科](https://zh.wikipedia.org/)
+ [菜鸟教程](https://www.runoob.com/)
+ [10分钟带你了解互联网是如何运作的！](https://www.bilibili.com/video/BV1Rz4y197Jd)
+ [浏览器是如何运作的？](https://www.bilibili.com/video/BV1x54y1B7RE/)
+ 官方文档
    + [Node.js](http://nodejs.cn/)
        + [npm](https://www.npmjs.cn/)
        + [Vue.js](https://cn.vuejs.org/)
        + [React](https://react.docschina.org/)
    + [Git](https://git-scm.com/book/zh/v2)
    + [Hexo](https://hexo.io/zh-cn/docs/index.html)
    + [Butterfly](https://butterfly.js.org/)

# 2.搭建本地博客开发环境

## 2.1 安装Git

下载链接：[Git](https://git-scm.com/downloads)

> 安装过程中建议把Git GUI和Git Bash添加到右键菜单的选项取消的
> 其他的一路默认即可

## 2.2 安装node.js

### 2.2.1 下载

下载链接: [node.js](https://nodejs.org/zh-cn/download/)

> 为啥下载node.js？
> 因为这个安装包也会安装npm，我们要用的就是npm

### 2.2.2 设置npm镜像源

因为npm的下载库来源于国外`(npmjs.org)`,速度极慢且不稳定，这里建议使用国内阿里云镜像

> npm config set registry https://registry.npm.taobao.org

### 2.2.3 npm全局安装Hexo

> npm install -g hexo-cli

### 2.2.4 查看Hexo是否安装成功

> hexo -v

## 2.3 搭建基础工作区

### 2.3.1 初始化

在你喜欢的地方新建一个文件夹`Blog`，并用VScode打开

按下`Ctrl`+`~`打开 命令行，输入：

> hexo init

成功安装后，目录如下

{% asset_img JustOneBlog-2021-04-18-11-09-40.png %}

### 2.3.2 生产静态页面

> hexo g

完成后会生成一个public文件夹，里面便是一个博客网站的内容部分

{% asset_img JustOneBlog-2021-04-18-11-13-01.png %}

### 2.3.3 开启本地服务器

> hexo s

输入完成之后 访问 http://localhost:4000，便有Hexo博客初始化的页面

{% asset_img JustOneBlog-2021-04-18-11-16-21.png %}

### 2.3.4 新建文章

> hexo new MyFirstBlog

输入之后source/_posts下会生成MyFirstBlog.md文件

{% asset_img JustOneBlog-2021-04-18-11-21-53.png %}

填写部分内容后，博客里便就多了一篇自己的文章

{% asset_img JustOneBlog-2021-04-18-11-23-25.png %}

## 2.4 使用Butterfly主题

### 2.4.1 安装Butterfly主题

> git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/Butterfly

> github.com最近不太安稳，经常被墙，这里建议大家自行寻找翻墙方法
> 提示: 需要配置git代理

安装完成后，会多出一个Butterfly的文件夹，里面会有其主题的内容及配置文件

{% asset_img JustOneBlog-2021-04-18-11-32-26.png %}

### 2.4.2 应用Butterfly主题

修改站点配置文件`_config.yml`，把主题改为butterfly

```yml
#theme: landscape
theme: butterfly
```

### 2.4.3 安装相关插件

> npm install hexo-renderer-pug hexo-renderer-stylus --save
> 这里建议再安装一个比较有用的插件 —— hexo-browsersync(游览器实时更新，方便预览效果)
> npm install hexo-browsersync --save

### 2.4.4 生成一个Butterfly主题的Hexo博客

> hexo clean  #清楚缓存文件
> hexo g      #生成发布用的静态页面
> hexo s      #重启本地服务器
> #以上指令之后经常用到

> 步骤没有错误的话，现在你已经成功应用主题

{% asset_img JustOneBlog-2021-04-18-11-45-57.png %}

> 想要得到各种特效和功能，请仔细参考[Butterfly文档](https://butterfly.js.org/)

{% asset_img JustOneBlog-2021-04-18-11-49-44.png %}

# 3.拥有一个云服务器

## 3.1 ~~(充钱)~~ 购买云服务器

下面例子讲的是vultr(国外)的服务器，但更推荐国内的[阿里云](https://cn.aliyun.com/)和[腾讯云](https://cloud.tencent.com/)，少走些弯路。

> [学生可以白嫖阿里云三个月！](https://developer.aliyun.com/adc/student/)
> 详细教程可以百度

{% asset_img JustOneBlog-2021-04-23-02-04-30.png %}

> 这里选择vultr，因为~~我穷~~vultr按小时计费(阿里云，腾讯云按月或者++计费)，能在我经济允许的情况下多开几个服务器

{% asset_img JustOneBlog-2021-04-23-01-52-31.png %}

花钱就不用介绍了，一般充钱最快最容易。

## 3.2 部署云服务器

### 3.2.1 选择云计算

{% asset_img JustOneBlog-2021-04-23-02-06-10.png %}

### 3.2.2 选择服务器地理位置

{% asset_img JustOneBlog-2021-04-23-02-07-07.png %}

> 选择你喜欢的地点

### 3.2.3 选择系统

{% asset_img JustOneBlog-2021-04-23-02-07-53.png %}

> 这里选用64位Centos系统，其他系统也可选择，操作过程中内容大同小异

### 3.2.4 选择服务器性能

{% asset_img JustOneBlog-2021-04-23-02-09-44.png %}

> 这里不建议选用只有IPv6的，选择$3.5/mo的套餐

### 3.2.5 成功部署

其他配置均不需要更改，如果点击右下角`(Deploy Now)`部署

{% asset_img JustOneBlog-2021-04-23-02-16-22.png %}

等待服务器安装完系统后，显示`Runing`即为部署成功

## 3.3 连接至云服务器

> TODO:串讲端口，IP，域名，常见端口，代理

### 3.3.1 提前准备

+ 端口 : TCP/IP协议，一个应用跑在一个端口上
    + [各种服务常用端口号](https://blog.csdn.net/zhanghuiyu01/article/details/80830045)
+ IP  : 网际互连协议。路由器在互联网下有唯一IP(公网)，联网设备在路由器下也有IP(局域网)
    + [干货：计算机网络中那些常见的IP地址]()
    + 127.0.0.1 : 本地地址 (仅对本机有效)
    + 192.168.x.x : 私有地址，设备在路由器下被分配的地址，可以通过此地址来经行分享文件，发送网络请求等操作。
+ 域名 : 通过DNS服务器解析出IP地址，再连接到此IP地址。
    + localhost : 本地地址 (`C:\Windows\System32\drivers\etc`下的hosts文件解析出的)
+ ssh : 安全外壳协议。通过xshell等工具用ssh协议连接上云服务器。
+ [FinalShell](https://www.hostbuf.com/t/988.html)<font color="red">(推荐)</font>: 强大的连接服务器的工具。

### 3.3.2 查看服务器的信息

打开vultr(阿里云/腾讯云)控制台，点击自己的服务器查看信息

{% asset_img JustOneBlog-2021-04-23-03-11-28.png %}

需要留意的是 <font color="red">IP 用户名(Username) 密码(Password)</font>

> linux会有一个`root`(超级管理员)账号，也注册有其他不同权限的账号

### 3.3.3 使用FinalShell连接服务器

打开FinalShell，打开连接设置，选择SSH

{% asset_img JustOneBlog-2021-04-23-03-23-32.png %}

填入喜欢的名称，填入IP,用户名,密码，<font color="red">勾选上智能加速</font>。

随后双击自己的服务器，连接服务器

{% asset_img JustOneBlog-2021-04-23-03-28-29.png %}

# 4.部署个人博客至服务器中

参考文章: [将Hexo部署到自己的服务器上](https://www.cnblogs.com/jie-fang/p/13445939.html)
## 4.1 提前准备

+ [nginx](https://www.runoob.com/w3cnote/nginx-setup-intro.html)：高性能的HTTP和反向代理web服务器。
+ [Git](https://git-scm.com)：这里使用Git来将服务器部署到服务器中
+ SSH密钥：是一种无须密码登录Linux实例的认证方式。

## 4.2 安装需要的环境

安装git
> sudo yum -y install git
安装nginx
> sudo yum -y install nginx 

## 4.3 添加git用户

> useradd git 
> passwd  git
> 
> #给git用户配置sudo权限
> chmod 740 /etc/sudoers
> vim /etc/sudoers
> 
> #找到root ALL=(ALL) ALL，在它下方加入一行
> git ALL=(ALL) ALL
> 
> chmod 400 /etc/sudoers

## 4.4 给git用户添加ssh密钥

> su - git
> mkdir -p ~/.ssh
> touch ~/.ssh/authorized_keys
> chmod 600 ~/.ssh/authorzied_keys
> chmod 700 ~/.ssh
> vim ~/.ssh/authorized_keys    #将ssh密钥粘贴进去

## 4.5 创建git仓库

> #新建目录，这是git仓库的位置
> sudo mkdir -p /var/repo    
> sudo mkdir -p /var/www/hexo
>
> #转到git仓库的文件夹
> cd /var/repo  
> 
> #创建一个名叫blog的仓库
> sudo git init --bare blog.git 
> sudo vim /var/repo/blog.git/hooks/post-update

编辑`post-update`文件内容如下：
> #!/bin/bash
> git --work-tree=/var/www/hexo --git-dir=/var/repo/blog.git checkout -f

给post-update授权:
> cd /var/repo/blog.git/hooks/
> sudo chown -R git:git /var/repo/
> sudo chown -R git:git /var/www/hexo
> sudo chmod +x post-update  #赋予其可执行权限

## 4.6 配置Nginx

> cd /etc/nginx/conf.d/
> vim blog.conf

`blog.conf`的内容如下:
``` conf
server {
    listen    80 default_server;
    listen    [::] default_server;
    server_name    207.148.18.185;
    root    /var/www/hexo
}
```

## 4.7 本地一键部署到服务器

> hexo d