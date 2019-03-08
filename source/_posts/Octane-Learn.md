---
layout:     post
title:      Octane 笔记
date:       2018-08-30
author:     Brywmzl
tags: [CINEMA 4D,Octane]
password: 
---
https://docs.redshift3d.com/display/RSDOCS

<!--more-->

# 渲染设置

![](/img/Learn/Octane/OctaneSetting.png)

## 渲染模式

* **Infochannels** 信息通道 [官方文档](http://www.aoktar.com/octane/InfoChannels.html)
* **Directlighting** 直接照明 （快速出效果）[官方文档](http://www.aoktar.com/octane/DirectLighting.html)
* **Pathtracing** 光线跟踪（影响速度{% emoji ant %}）[官方文档](http://www.aoktar.com/octane/PathTracing.html)
* **PMC** [官方文档](http://www.aoktar.com/octane/PMC.html)

---

* **Max.samples** 最大采样
* **Diffuse depth** 漫反射深度
* **Specular depth** 反射深度
* **Ray epsilon** 
* **Filter size**
* {% emoji ballot_box_with_check %} **Alpha shadows**
* **Caustic blur**  
* **GI clamp** 

---

## 基本参数

**Adaptive Sampling** 自适应采样

* 勾上会快点

**keep environment** 字面好像是保持环境

* 去除开启Alpha channel带来的白边
* redshift也有同样的症状

**Affect Alpha** 影响Alpha

* 为什么开启Alpha channel 玻璃材质还是不透明的原因

---
# 节点
## Dirt 脏
* 在我看来他就是redshift的ao节点
* 增强自身投影用的
* 参数...

---

## DayLight 参数

**Turbidity** 浊度

* 顾名思义 空气大气的尘埃 浑浊
* 阴天就是很浑浊

**Power** 功率

* 好像是指灯光强度

**North Offset** 北边偏移

* 相当于对H进项旋转

**Sun size** 阳光大小

* 该参数越大投影边缘越虚 说白了就是羽化边缘

**New Model** 新模式

* 新模式有一点好 就是模拟现实 根据角度来定义色温（冷暖）
* 当然喜新厌旧啦 这还用说 这个选项估计是给那些还在怀旧的老司机用的

**Ground** 背景

* Ground start angle  （背景开始角度）相当于Y轴偏移
* Ground blend angle （背景混合角度）这个就更好理解了模糊羽化

# Volumetrics（体积）

* [What is Volumetrics（什么是体积）](http://www.aoktar.com/octane/WhatisVolumetrics.html)

# Octane Scatter

* [官方文档](http://www.aoktar.com/octane/InterfaceSettings1.html)

# Octane Object Tag（对象标签）

* [Interface & Settings（界面&设置）](http://www.aoktar.com/octane/InterfaceSettings1.html)