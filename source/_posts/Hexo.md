﻿---
layout: post
title: Hexo搭建与改造
date: 2018-10-09
updated:
comments: false
tags: 
categories: 
permalink: 
password: 
---

界面调整 部分页面出现渲染不出来的现象 以后将慢慢改进

<!--more-->

<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=234023&auto=1&height=66"></iframe>

# 概述

## 为啥我要换Theme？

当我第一次听到[Hexo](https://hexo.io)有点懵，后面看了[大佬](https://imys.net)的博客
我才意识到Hexo+Theme的强大
简单介绍下
Hexo是基于NodeJs的静态博客框架，简单、轻量，其生成的静态网页可以托管在Github上。

比起之前那个。。。。。好太多~
之所有我选Hexo主要原因有以下几点：

* 1.我选择hexo的最大理由就是可以插入html，就像头上那个网易云音乐（非主流qq空间必备）
* 2.Markdown的美观性和自由度远远大过之前那个。。。。
* 3.最让我心动的是居然可以自定义页面，在我的about页面里可以看到
* 4.对之前Markdownw文件还是兼容的挺好，入乡随俗，就是部分渲染需要稍作调整
* 5.丰富的插件，尤其是emoji，太不可思议了{% emoji smiley %}
* 6.有了搜索功能，再也不用一个一个找或者用网页的搜索功能
* 7.标签和分类都有
* 8.对手机界面的适应也是美美哒~

## 相关链接

[Hexo 官网](https://hexo.io)
[indigo Github](https://github.com/yscoder/hexo-theme-indigo)

# 环境部署

我部署是参考{% link Hexo 博客搭建指南 https://github.com/limedroid/HexoLearning %}

## 安装Git和NodeJs

[Git 官网下载](https://git-scm.com/downloads)
[NodeJs 官网下载](https://nodejs.org/en/download)
{% codeblock 检验NodeJs安装成功（成功会返回版本号） https://hexo.io/docs/#Install-Node-js Install Node.js 官方文档 %}
$ node -v
{% endcodeblock %}

# Hexo

## 安装Hexo

{% codeblock 右键 "Git Bash Here" https://hexo.io/docs/#Installation Installation Install Hexo 官方文档 %}
$ npm install hexo-cli -g
{% endcodeblock %}

{% codeblock 注意：Mac系统，则需要 %}
$ sudo npm install hexo-cli -g
{% endcodeblock %}

{% codeblock Setup https://hexo.io/docs/setup Setup 官方文档 %}
$ hexo init Brywmzl.github.io # 创建文件夹
$ cd Brywmzl.github.io # 打开文件夹
$ npm install # 安装
{% endcodeblock %}

## 生成静态页面

{% codeblock 清除 就是删除生成的文件夹 避免出错 %}
$ hexo clean 
{% endcodeblock %}

{% codeblock 生成顾名思义不说了 https://hexo.io/docs/generating generating 官方文档 %}
$ hexo g # generating
{% endcodeblock %}

## 本地运行
{% codeblock server 在本地运行（默认：localhost:4000） https://hexo.io/docs/server server 官方文档 %}
$ hexo s # server
{% endcodeblock %}

{% codeblock 如果要更改端口或遇到 EADDRINUSE 错误，请使用该 -p 选项设置其他端口。 https://hexo.io/docs/server#Custom-IP Custom IP 官方文档 %}
$ hexo server -p 5000
{% endcodeblock %}

{% codeblock 命令也可以连着 %}
$ hexo clean && hexo g && hexo d
{% endcodeblock %}

## 配置Hexo

网站的设置大部分都在`_config.yml`文件中，详细配置可以查看[官方文档](https://hexo.io/zh-cn/docs/configuration.html)
* title -> 网站标题
* subtitle -> 网站副标题
* description -> 网站描述
* author -> 您的名字
* language -> 网站使用的语言(写zh-cn也不起作用，官方文档也没详细说明)

# indigo Theme

运行后你会发现默认的主题很怂，具体有多怂我这里也没法形容{% emoji fearful %}

1.下载主题 [hexo-theme-indigo](https://github.com/yscoder/hexo-theme-indigo/releases)
2.解压到Theme文件夹
3.在`_config.yml`文件中改`theme: indigo`（文件夹的名字）
4.[安装](https://github.com/yscoder/hexo-theme-indigo/wiki/%E5%AE%89%E8%A3%85)（执行步骤3在安装里的前两个步骤可以省略）

## 配置Theme
{% emoji -1 %}

{% codeblock 新建 %}
$ hexo new post # 新建post文章
$ hexo new page pageName # 自定义页面
{% endcodeblock %}

前者执行命令后会在你的 Hexo 根目录 `source/_posts` 的文件夹，生成一个md文件。
后者执行命令后会在你的 Hexo 根目录 `source/` 目录下生成一个与你刚才输入的 `pageName` 一样的文件夹，里面只有一个 `index.md`。
如果文件存在会变成`index-1.md`

<br>{% emoji warning 48 %}如果发布后发现文章或页面出现乱码
主要原因就是Markdown文件需要以UTF-8编码

颜色配置
https://github.com/yscoder/hexo-theme-indigo/issues/387
颜色参考
http://www.materialpalette.com/

# 在Github搭建Hexo

## 设置Github项目名称
就是项目名为 `用户名.Github.io`
搭建过的都知道，不详细说明

## 出现问题
重装系统后可能导致两个问题
一个是github的登录没掉了，还有一个就是git的配置
git 只需改环境变量 这个百度有
而登录的话发现https登录的时候产生问题了，所以改用生产 ssh密钥
[hexo迁移重装](http://shomy.top/2017/01/27/hexo-migrate-solution/)

### 生成 ssh 密钥
`ssh-keygen -t rsa -C "用户名"`
生成过程中需要输入两次密码
而在git里输入密码时不显示的
然后去github自己头像下面有个setting 里添加
然后登录的时候`_config.yml`需要改成
```
deploy:
  type: git
  repo: ssh://git@github.com/Brywmzl/Brywmzl.github.io.git
  branch: master
```
提交的时候会提醒输入密码~

# 附加

## 菜单icon运用

https://fontawesome.com/icons
名称查看（新版本图标不可用）
http://fontawesome.dashgame.com/

## emoji插件

[hexo-tag-emojis](https://github.com/sergiolepore/hexo-tag-emojis)
需要在 hexo 的生成阶段把文章中的 emoji 标记渲染为图片或者 emoji 字体图标
[emoji 名称查看](http://www.emoji-cheat-sheet.com/)


> {% emoji ambulance 48 %} {% emoji 1234 48 %}<br>

{% codeblock %}
{% raw %}{% emoji ambulance 48 %} {% emoji 1234 48 %}{% endraw %}
{% endcodeblock %}

> {% emoji_block %}
博客界面进行调整 导致部分界面无法按照原来的主题进行渲染 :alien:<p>
本次改用Hexo博客 主题是indigo :alien:<br>
{% endemoji_block %}

{% codeblock %}
{% raw %}{% emoji_block %}
博客界面进行调整 导致部分界面无法按照原来的主题进行渲染 :alien:<p>
本次改用Hexo博客 主题是indigo :alien:
{% endemoji_block %}{% endraw %}
{% endcodeblock %}

## 文章加密插件

***都不是很好用***
https://github.com/MikeCoder/hexo-blog-encrypt （目录渲染不出来）
https://github.com/edolphin-ydf/hexo-encrypt

# 页面

## 页面渲染

**表格**

| 表头1|表头2|表头3|表头4
|-| :- | :-: | -: |
|默认左对齐|左对齐|居中对其|右对齐|
|默认左对齐|左对齐|居中对其|右对齐|
|默认左对齐|左对齐|居中对其|右对齐|

**图片按钮**

{% codeblock %}
{% raw %}[!{% endraw %}{% raw %}[Watch the video](https://raw.github.com/GabLeRoux/WebMole/master/ressources/WebMole_Youtube_Video.png)](http://youtu.be/vt5fpE0bzSY){% endraw %}
{% endcodeblock %}

被渲染成{% emoji point_down 30 %}

{% codeblock %}
[![Watch the video[Watch the video](https://raw.github.com/GabLeRoux/WebMole/master/ressources/WebMole_Youtube_Video.png)](http://youtu.be/vt5fpE0bzSY)
{% endcodeblock %}

只能选用html替代{% emoji point_down 30 %}

{% codeblock %}
<a href="https://youtube.com"><img src="https://raw.github.com/GabLeRoux/WebMole/master/ressources/WebMole_Youtube_Video.png"></a>
{% endcodeblock %}

[参考](http://www.wibibi.com/info.php?tid=117)

<a href="https://youtube.com"><img src="/img/post-bg-os-metro.jpg"></a>

**图片**

{% img cat https://placekitten.com/50/50 50 50 猫 喵喵喵 %}

{% codeblock %}
{% raw %}{% img cat https://placekitten.com/50/50 50 50 猫 喵喵喵 %}{% endraw %}
{% endcodeblock %}

![猫 喵喵喵](https://placekitten.com/50/50)

{% codeblock %}
{% raw %}!{% endraw %}[猫 喵喵喵](https://placekitten.com/50/50)
{% endcodeblock %}

---

**字体**

*这里是斜体*
**这里是粗体**
***这里是粗体 + 斜体***

---

**注释符号**

```card
{% raw %}
{% endraw %}
```

```
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=red>我是红色</font>
<font color=#008000>我是绿色</font>
<font color=Blue>我是蓝色</font>
<font size=5>我是尺寸</font>
<font face="黑体" color=green size=5>我是黑体，绿色，尺寸为5</font>
<strong><font size=5>我是加粗</font></strong>
<a href="链接"><strong><font color=37668b>标题</font></strong></a>
<div align="right"><strong><font size=5 color=0470a1>标题</font></strong></div>
```

left：左对齐内容。
right：右对齐内容。
center：居中对齐内容。
justify：对行进行伸展，这样每行都可以有相等的长度（就像在报纸和杂志中）。

[原文](https://blog.csdn.net/heimu24/article/details/81189700)
[](http://www.w3school.com.cn/tags/att_div_align.asp)

## 自定义页面

[自定义页面](https://gist.github.com/yscoder/0fd1332c2b8bef21115cbaa20f11d7ce)
自定义页面还存在很多问题（例如图片被拉伸来强制适应card）

## 支持 html 后就是爽~

直接复制 html代码直接可用
https://fontawesome.com/icons



{% youtube MlQoqO7MJ7Q %}

{% codeblock 官方提供的标签 https://hexo.io/docs/tag-plugins#YouTube 官方文档 %}
{% raw %}{% youtube video_id %}
{% vimeo video_id %}{% endraw %}
{% endcodeblock %}

{% codeblock 窄屏 %}
<iframe width="666" height="400" src="https://www.youtube.com/embed/MlQoqO7MJ7Q" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
{% endcodeblock %}

{% codeblock 宽屏 %}
<iframe width="900" height="560" src="https://www.youtube.com/embed/MlQoqO7MJ7Q" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
{% endcodeblock %}

# 改造
[Hexo主题配置与优化（二）](https://starwindy.oschina.io/2015/05/06/Hexo主题配置与优化（二）)

修改标签显示的标题 `\themes\indigo\layout\_partial\head.ejs`
{% codeblock %}
    <title><% if (title){ %><%= title %> | <% } %><%= config.title %><% if (config.subtitle){ %> | <%= config.subtitle %><% } %></title>
{% endcodeblock %}

{% codeblock 我改这样 %}
<title><% if (title){ %><%= title %> | <% } %><%= config.title %></title>
{% endcodeblock %}

修改dark `\themes\indigo\layout\_partial\head.ejs`

修改配色 `\source\css\_partial\variable.less`

{% blockquote 配色 http://www.materialpalette.com 参考 %}
primaryColor: 主色调
darkPrimaryColor: dark主色调
{% endblockquote %}

修改头像大小描边 `\source\css\_partial\layout.less`

{% blockquote .avatar %}
border: 描边的粗细
border-radius: 描边半径（这里不是半径的意思0%-49%圆角 %50%-100%是圆）
{% endblockquote %}

{% blockquote .brand %}
padding: 头像背景的高度
background: （头像后面的背景颜色，不透明度）
{% endblockquote %}

修改自定义页面 `\themes\indigo\source\css\_partial\page.less`

{% blockquote %}
border-bottom: 最底下的分割线
img: 改了img的width和height为空就可以解决图片拉伸问题
{% endblockquote %}

{% blockquote .page-article %}
padding: 10px; 最外边距
.card(3px); 卡片圆角
{% endblockquote %}

{% blockquote .page-content %}
    figure {
        padding: 20px!important;
    } 图相框的边距
{% endblockquote %}

{% blockquote 作者 https://brywmzl.github.io Brywmzl %}
content
{% endblockquote %}