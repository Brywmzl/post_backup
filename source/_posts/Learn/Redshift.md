---
layout:     post
title:      Redshift 笔记
subtitle:   https://docs.redshift3d.com/display/RSDOCS
date:       2018-08-30
author:     Brywmzl
header-img: img/RedShift/261331074269.jpg
catalog: true
tags: [CINEMA 4D,Redshift]
password: 
---
https://docs.redshift3d.com/display/RSDOCS

<!--more-->

# [Cameras（摄像机）](https://docs.redshift3d.com/display/RSDOCS/Cameras)

# [Lights（灯光）](https://docs.redshift3d.com/display/RSDOCS/Lights)
<iframe src="//player.bilibili.com/player.html?aid=24157471&cid=40486493&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" height="530" width="670">> </iframe>
# [Shader（着色器节点）](https://docs.redshift3d.com/display/RSDOCS/Shaders)

## [Material Shaders（材质）](https://docs.redshift3d.com/display/RSDOCS/Material+Shaders)

## [Textures Shaders（纹理）](https://docs.redshift3d.com/display/RSDOCS/Noise+Texture)

### Color
This tab allows you to control how the internally computed noise is turned into color for output.
这个标签允许你控制内部计算的噪波如何转换为输出颜色。

### Noise
This tab allows you to control how the noise is generated.
这个标签允许你控制噪波的生成。

#### General（通用）
* Noise Type（噪波类型）
	* Fractal（分形）
	* Turbulence（湍流）
	* Cell（蜂窝）

#### Fractal/Turbulence（分形/湍流）
* Complexity（复杂）
* Amplitude Gain（振幅增益）有点像羽化
* Frequency Scale（频率缩放）就是缩放
* Distortion（失真）好像是扭曲又好像移动
* Distortion Scale（失真缩放）

#### Time

##### Source（源）

Allows you to control how the noise is affected over time. The options are as follows:
* None - 不考虑时间计算
* Constant（常量） - 当前帧时间来计算
* User - 用户定义的时间来计算

##### Constant
这是应用于当前帧时间的比例。仅在Source设置为“常量”时适用

##### Consant Scale
This is a scale that is applied to the current frame time. Only applicable when Source is set to 'Constant'.

##### User Time
This is the user-defined time value. Only applicable when Source is set to 'User'.

## Color

### Color Layer

# Volume Topics
## [Volumetric Scattering And Fog（体积光和雾）](https://docs.redshift3d.com/display/RSDOCS/Volumetric+Scattering+And+Fog)
<iframe src="//player.bilibili.com/player.html?aid=24632282&cid=41401990&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" height="530" width="670"> </iframe>

# 渲染设置
## 基本
<a href="https://docs.redshift3d.com/display/RSDOCS/Motion+Blur"><strong><font face="微软雅黑" size=5 color=ed1c24>运动模糊</font></strong></a>
<a href="https://docs.redshift3d.com/display/RSDOCS/Motion+Blur#MotionBlur-EnableDeformationBlur"><strong><font face="微软雅黑" size=4 color=ed1c24>Enable Deformation Blur（启用变形模糊）</font></strong></a>
Deformation blur (tracking the motion of vertices) can be memory-intensive especially for high-poly or displaced geometry. For this reason, it has a separate switch to enable/disable. If most of your scene's motion is due to rigid body animation or camera movement, you can leave this option disabled.
<strong><font face="微软雅黑" size=4 color=ed1c24>Transformation Steps（转型步骤）</font></strong>
这个数值越大，过渡约圆滑（如图所示）
<img src="/img/Learn/Redshift/0.png" />

---

<strong><font face="微软雅黑" size=4 color=ed1c24>Frame Duration（帧持续时间）</font></strong>
这个参数和Oc的 <font face="微软雅黑" size=3 color=55b103>Shutter[sec.]（快门）</font> 是一样的，越大越模糊

---

<strong><font face="微软雅黑" size=4 color=ed1c24>Shutter Position（快门位置）</font></strong>
这个参数和Oc的 <font face="微软雅黑" size=3 color=55b103>Shutter alignment（快门对齐）</font>是一样的，就连选项都一样 这个翻译的有点抽象，其实也很好理解

|Shutter Position(Reshfit)|Shutter alignment(Octane)|描述
|::-|::-|:-:
|<font size=4 color=ed1c24>Center on Frame</font>|<font face="微软雅黑" size=3 color=55b103>Centered</font>|中
|<font size=4 color=ed1c24>Start on Frame</font>|<font face="微软雅黑" size=3 color=55b103>Before</font>|前
|<font size=4 color=ed1c24>End on Frame</font>|<font face="微软雅黑" size=3 color=55b103>After</font>|后

不过 Redshift 有一点好就是，可以用 <font face="微软雅黑" size=3 color=ed1c24>Start on Frame</font> 和 <font face="微软雅黑" size=3 color=ed1c24>End on Frame</font> 这两个参数控制开始和结束的多少

---

<a href="https://docs.redshift3d.com/display/RSDOCS/Motion+Blur#MotionBlur-ShutterEfficiency"><strong><strong><font face="微软雅黑" size=4 color=ed1c24>Shutter Efficiency（快门效率）</font></strong></a>
这个参数最大值1，比较难解释（如图所示）
<img src="/img/Learn/Redshift/1.png" />

## AOV（任意输出变量）
AOV stands for "arbitrary output variables"
<iframe src="//player.bilibili.com/player.html?aid=24981571&cid=42201458&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" height="530" width="670"> </iframe>

## Optimization（优化）

## GI（全局光照）
GI 全称 "Global Illumination"
* 66