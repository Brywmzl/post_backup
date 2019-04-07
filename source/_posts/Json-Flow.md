---
layout:     post
title:      Json Flow
date:       2019-01-13
author:     Brywmzl
tags: []
categories: [Brywmzl]
---
Json Flow是一键处理json安排事件的工具，通常用于补丁制作。

<!--more-->

![](/img/json_flow/0.png)  

# 下载
>- 暂不提供下载，也没有版本号，更新版本丢失

# 更新日志
* 即将更新内容
	* 添加判断  `?process[]?`
	* 添加常量  `$input` （手动输入，以及文件拖拽）
	* 添加动作  `dir_del`（删除目录）
	* 添加动作  `reg_del`（删除注册表）
	* 添加动作  `Patch`（增强补丁）
	* 添加动作  `dir_creat`（创建目录支持list）
	* 更改常量  `set_reg`  和 `del_reg`
	* 修复常量  `$get_dir[]`
	* 修复动作  `process_check`
	* 修复 windows10 拖拽问题
* 0.00
	* 支持list文件（替代数组）
	* 继续完善
	* 修复bug。。。
	* 构造基本完成！

# 结构
begin_action（程序初始化）
{% emoji point_down 30 %}
components_list（功能列表）
{% emoji point_down 30 %}
end_action（退出程序后）

# 自定义 action
自定义 action 可以通过在 json 二级以自定义 action 名称，即可在 `run_action` 被调用。

# actions
## file（文件类）
{% codeblock 复制文件（支持 list） %}
{
"action_type":"file_copy",
"file_name":"$get_variable[install_path]\\theme\\build.xml",
"type":"multi",
"copy_to":"\\theme\\build.xml.backup"
}
{% endcodeblock %}
{% codeblock 删除文件（支持 list） %}
{
"action_type": "file_del",
"file_name":"$rundir\\_res\\var.ini"
}
{% endcodeblock %}
{% codeblock 文件重命名（支持 list） %}
{
"action_type":"file_rename",
"type":"multi",
"file_name":"$get_variable[install_path]\\theme\\build.xml.backup",
"rename_to":"build.xml"
}
{% endcodeblock %}
{% codeblock 替换文本文件中的内容（暂不支持 list） %}
{
"action_type":"file_replace_text",
"file_name":"$get_variable[install_path]\\theme\\build.xml",
"find_text":"<AdWraperMid.+bounds=\"(.+)\"",
"replace_with":"0,0,0,0",
"case_sensitive":"1",
"regular_expression":"1"
}
{% endcodeblock %}
---
type="","solo"；"multi"（支持.list列表文件，默认：Solo）
当 type=multi 时 file_name 就为 list 文件名称
当 action 有两个参数请，list 文件了用英文逗号分隔开，（file_name,renmae_to）

## dir（目录类）
{% codeblock 创建目录（暂不支持 list） %}
{
"action_type":"dir_creat",
"dir":"%UserName%\\AppData\\Local\\youdao\\Ynote\\Ad"
}
{% endcodeblock %}
{% codeblock 删除目录（支持 list） %}
{
"action_type":"dir_del",
"file_name":"file_name",
"type":"multi",
"dir":"%UserName%\\AppData\\Local\\youdao\\Ynote\\Ad"
}
{% endcodeblock %}
{% codeblock 复制目录（支持 list） %}
{
"action_type":"dir_copy",
"file_name":"file_name",
"type":"multi",
"dir":"%UserName%\\AppData\\Local\\youdao\\Ynote\\Ad",
"copy_to":"%UserName%\\AppData\\Local\\youdao\\Ynote\\Ad"
}
{% endcodeblock %}
---
当 type=multi 时 dir 就为 list 文件名称

## message（信息框类）
{% codeblock 选择型信息框 %}
{
"action_type": "message_select",
"caption":"补丁完成",
"content":"是否重启 \"有道云笔记\"？",
"run":[
	{
	"action_type":"process_end",
	"process_name":"YoudaoNote.exe"
	},
	{
	"action_type":"open_url",
	"url":"$get_variable[install_path]\\YoudaoNote.exe"
	}
]
}
{% endcodeblock %}

{% codeblock 信息框 %}
{
"action_type": "message",
"caption":"补丁已还原！",
"content":"是否重启 \"有道云笔记\"？"
}
{% endcodeblock %}

## process（进程类）
{% codeblock 终止进程 %}
{
"action_type":"process_end",
"process_name":"YoudaoNote.exe"
}
{% endcodeblock %}

{% codeblock 查询进程（目前版本不支持） %}
{
"action_type":"process_check",
"process_name":"YoudaoNote.exe"
}
{% endcodeblock %}

## reg（注册表类）
{% codeblock  写到注册表 %}
{
"action_type":"set_reg",
"path":"全路径",
"value":"值"
}
{% endcodeblock %}
{% codeblock  删除注册表（目前版本不支持） %}
{
"action_type":"del_reg",
"path":"路径"
}
{% endcodeblock %}

## url（打开地址）
{% codeblock  打开地址 %}
{
"action_type":"open_url",
"url":"地址"
}
{% endcodeblock %}

## set_variable（变量类）
{% codeblock  设置变量 %}
{
"action_type":"set_variable",
"name":"install_status",
"variable":"不可用"
}
{% endcodeblock %}

## if（判断类）
{% codeblock  如果语句 %}
{
"action_type":"if",
"content":"?reg[HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Youdao\\YoudaoNote\\Install]?",
"type":"exist",
"value":"1",
"run":[
	{
	"action_type":"set_variable",
	"name":"install_status",
	"variable":"可用"
	},
	{
	"action_type":"set_variable",
	"name":"install_path",
	"variable":"$get_reg_x64[HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Youdao\\YoudaoNote\\Install]"
	}
],
"else_run":[
	{
	"action_type":"set_variable",
	"name":"install_status",
	"variable":"不可用"
	}
]
}
{% endcodeblock %}

## host（host类）

{% codeblock  添加 host（支持 list） %}
{
"action_type":"hosts_add",
"type":"multi",
"hosts":"$rundir\\_res\\hosts.list"
}
{% endcodeblock %}

{% codeblock  删除 host（目前版本不支持） %}
{
"action_type":"hosts_del",
"type":"multi",
"hosts":"$rundir\\_res\\hosts.list"
}
{% endcodeblock %}

## Patch（补丁类）

{% codeblock  增强补丁（目前版本不支持） %}
{
"action_type":"Patch",
"config":"配置文件",
"list":"$rundir\\_res\\hosts.list"
}
{% endcodeblock %}

---
smart_backup（只能备份 逻辑型）
output_content（输出过程 逻辑型）

## zip（压缩类）
{% codeblock zip 压缩 %}
{
"action_type":"zip",
"files":"文件夹或文件名",
"file_name":"zip文件名"
}
{% endcodeblock %}
{% codeblock zip 解压 %}
{
"action_type":"unzip",
"file_name":"zip文件名",
"files":"解压到目录"
}
{% endcodeblock %}

## 单行 action

{% codeblock  输出文本 %}
"print":"输出内容"
"print":0（清空）
{% endcodeblock %}

{% codeblock  简单信息框 %}
"message":"内容"
{% endcodeblock %}

{% codeblock  选项卡切换（第一个为0，属性为对象） %}
"to_panel":0
{% endcodeblock %}

{% codeblock  设置剪辑板文本 %}
"set_clipboard":"内容"
{% endcodeblock %}

{% codeblock  终止任务 %}
"run_end":true
{% endcodeblock %}

{% codeblock  关闭程序 %}
"close":true
{% endcodeblock %}

{% codeblock  设置标题 %}
"set_caption":"内容"
{% endcodeblock %}

{% codeblock 设置按钮名称 %}
"button_caption":"内容"
{% endcodeblock %}

{% codeblock 设置背景图片 %}
"set_background":"图片路径"
{% endcodeblock %}

{% codeblock 运行 action %}
"run_action":"action 名称"
{% endcodeblock %}

# 常量
**$desktop**（桌面）
**$rundir**（运行目录）
**$windows_system**（windows系统目录）
**$windows**（windows安装系统）
**$temp**（临时目录）
**$get_clipboard**（获取剪辑板文本）
**$input**（手动输入，以及文件拖拽）
**$file**（选择文件）
**$get_reg[全路径]**（读取32位注册表）
**$get_reg_x64[全路径]**（读取64位注册表）
**$get_variable[变量名]**（读取变量）
**$get_dir[]**（从路径目录）
**$get_md5[]**（读取文件md5）
**%UserName%**（和 Windows 取用户路径一样）

# 逻辑
{% codeblock 功能列表显示逻辑判断 %}
"show_content" : "?file[$get_variable[install_path]\\theme\\build.xml.backup]?",
"show_type" : "exist",
"show_value":"0",
{% endcodeblock %}

{% codeblock if 逻辑判断 %}
"content":"?reg[HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Youdao\\YoudaoNote\\Install]?",
"type":"exist",
"value":"1",
{% endcodeblock %}

**content（用于判断是否存在）**
?file[]?
?dir[]?
?reg[]?

**type**
exist（存在）
include（包含）
equals（等于）

**value**
0=true
1=false
包括值

## list
.list就是一个列表文件，假设说你有多个文件需要执行同一个操作，你就可以利用list以换行的方式分割到数组来批量执行。前提是action要支持该类型