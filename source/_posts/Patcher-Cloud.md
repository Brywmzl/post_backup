---
layout:     post
title:      Patcher Cloud
date:       2019-01-24
author:     Brywmzl
catalog: true
tags: []
categories: [Brywmzl]
---
这是一个我一直很想写的补丁工具，我想将它和Json Flow相结合，这也是zer0cod3大神补丁给我带来的启发，因为Adobe CC2019的补丁贼大的原因（约200MB）做成集成补丁相当庞大，下载也相当麻烦，所以我想说做一个在线离线都能用的补丁，尽可能做到精确定位以及，自动化识别路径，一键通杀，敬请期待吧！

<!--more-->

![](/img/Brywmzl/PatcherCloud.png)

# 更新说明

* 基本框架已定
* 支持本地和url的json文件
* 支持属性复写(name不会被复写以外 其他都靠自觉)
* 支持数组目录
* 支持rar zip解压
* 可自定义缓存路径（默认:\_Temp）
* json数据
	* name（名称）
	* updat_date（更新时间）
	* remarks（备注说明内容）
	* install_path（和 json flow 一样支持用变量）
	* md5（文件md5用来作为唯一的标志认证如果已经补丁过了就没有必要在此下载）
	* process_end（补丁前需要杀掉的进程，目前只支持单个）
	* patch（补丁位置，目前只支持单个）
	* 之后再考虑要不要加一个action可以做到备份和恢复补丁功能 目前就先这样吧
* 还有明天再写吧

* 今天突发奇想 构造稍微改了下 做成了安装包的形式，不在兼容本地模式，考虑到多重补丁，需要设置多个变量为路径，并且支持action节点，后面将会陆续改良，敬请期待吧！~