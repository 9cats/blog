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

+ [Hexo](https://hexo.io/zh-cn/)是一款基于 Node.js 用于快速搭建博客的框架，有了它就可以完成完成个人博客的构建，它会帮你构建博客的整个框架，你只需要会使用Markdown 写博客即可。关于Hexo的具体介绍，可以在其官方网站查看具体的说明。
+ [Butterfly](https://butterfly.js.org/)Butterfly 博客主题。A Simple and Card UI Design theme for Hexo.
+ [Node.js](http://nodejs.cn/) 是一个基于Chrome V8引擎的JavaScript运行环境。安装好node.js后利用npm包管理工具来安装Hexo
+ [Git](https://git-scm.com)是目前世界上最先进的分布式版本控制系统（没有之一）。这里我们使用git bash 完成安装，初始化，上传等操作。

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