---
layout:     post
title:      Rename
date:       2019-01-12
author:     Brywmzl
tags: []
categories: [Brywmzl]
---
Rename是一款运用内置规则静默批量重命名的工具

<!--more-->

![](/img/Brywmzl/Rename.png)

# 下载
> [Rename.7z](https://www.lanzous.com/i2v1iwj)

# 规则
add 叠加文件名
del 删除节（1.分割符号 2.节顺序）
replace 替换（1.文本或正则表达式 2.替换为内容,可以是变量）
extension 重写扩展名（1.扩展名）

# 变量
<yy><MM><dd><HH><mm><ss> 年月日时分秒
<index> 索引（1.补零）
<sequence> 序列
<raw> 原文件名称

# 更新日志
* 1.00
	* 变更了规则
	* index 支持补零
	* 支持扩展名重写
	* 支持将文件创建为副本
	* 支持正则表达式替换
	* 支持保存成配置
* 0.00
	* 修复 windows10不能拖拽问题
	* 支持 "index" 变量