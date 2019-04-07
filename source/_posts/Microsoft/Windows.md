---
layout:     post
title:      Microsoft Windows
date:       2019-03-28
author:     Brywmzl
tags: [Microsoft,KMS,微软]
categories: []
---
https://www.microsoft.com

<!--more-->

# Windows 7

|版本|文件
|:-:|:-:
|旗舰版 X86|[7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_ULTIMATE_x86FRE_en-us.iso](http://download.microsoft.com/download/1/E/6/1E6B4803-DD2A-49DF-8468-69C0E6E36218/7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_ULTIMATE_x86FRE_en-us.iso)
|旗舰版 X64|[7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_ULTIMATE_x64FRE_en-us.iso](http://download.microsoft.com/download/5/1/9/5195A765-3A41-4A72-87D8-200D897CBE21/7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_ULTIMATE_x64FRE_en-us.iso)
|专业版 X86|[7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_PROFESSIONAL_x86FRE_en-us.iso](https://download.microsoft.com/download/C/0/6/C067D0CD-3785-4727-898E-60DC3120BB14/7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_PROFESSIONAL_x86FRE_en-us.iso)
|专业版 X64|[7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_PROFESSIONAL_x64FRE_en-us.iso](http://download.microsoft.com/download/0/6/3/06365375-C346-4D65-87C7-EE41F55F736B/7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_PROFESSIONAL_x64FRE_en-us.iso)
|家庭高级版 X86|[7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_HOMEPREMIUM_x86FRE_en-us.iso](http://download.microsoft.com/download/E/D/A/EDA6B508-7663-4E30-86F9-949932F443D0/7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_HOMEPREMIUM_x86FRE_en-us.iso)
|家庭高级版 X64|[7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_HOMEPREMIUM_x64FRE_en-us.iso](http://download.microsoft.com/download/E/A/8/EA804D86-C3DF-4719-9966-6A66C9306598/7601.24214.180801-1700.win7sp1_ldr_escrow_CLIENT_HOMEPREMIUM_x64FRE_en-us.iso)
|X86 简体中文语言包|[windows6.1-kb972813-x86-zh-cn_ab024143b556395e6638e26712b1e0f3bc031fcf.exe](http://download.windowsupdate.com/msdownload/update/software/updt/2009/08/windows6.1-kb972813-x86-zh-cn_ab024143b556395e6638e26712b1e0f3bc031fcf.exe)
|X64 简体中文语言包|[windows6.1-kb2483139-x64-zh-cn_2c1884b4fdf6c8e91986369d88bbcaae01c6f187.exe](http://download.windowsupdate.com/msdownload/update/software/updt/2011/02/windows6.1-kb2483139-x64-zh-cn_2c1884b4fdf6c8e91986369d88bbcaae01c6f187.exe)

# 其他
## 如何获取Win10最高管理员权限
* 打开组策略（`gpedit.msc`）
* 计算机配置 {% emoji point_right %} Windows 设置 {% emoji point_right %} 安全设置 {% emoji point_right %} 本地策略 {% emoji point_right %}
	* {% emoji no_entry %} 禁用“ 用户账户控制：以管理员批准模式运行所有管理员”
	* {% emoji no_entry %}  禁用“ 用户账户控制：用于内置管理员账户的管理员批准模式”

[原文](https://blog.csdn.net/yanhanhui1/article/details/82746357)

## 如何用防火墙屏蔽软件联网
**方法1**
* 必须打开防火墙
* 打开“Windows Defender防火墙”（`WF.msc`）
* 出站 {% emoji point_right %} 新建规则 {% emoji point_right %} 程序（然后找到他。。。） {% emoji point_right %} {% emoji no_entry_sign %} 阻止

**方法2**
* 必须打开防火墙
* 打开 `控制面板\系统和安全\Windows Defender 防火墙\允许的应用`
* 允许其他应用（然后找到他。。。）网络类型都选上
* 取消该程序前面的对勾

[原文](https://jingyan.baidu.com/article/f25ef25410e4ee482d1b8211.html)