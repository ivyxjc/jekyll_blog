---
layout: post
title: jspdirectives_md
category: 
tags: [javawebgitbook ]
keywords:
description:
---
# JSP指令元素
 
## 指令分类
JSP指令主要有三种：

**page指令**：通常位于jsp页面顶端，同一个页面可以有多个page指令<br>
**include指令**：将一个外部文件嵌入到当前JSP文件中，同时解析而这个页面中的JSP语句<br>
**taglib指令**：使用标签库定义新的自定义标签，在JSP页面中启用定制行为

## page指令
语法:

```jsp
<%@page 属性1="属性值" 属性2="属性值1,属性值2"...
        属性n="属性值n"%>
```

一共有13个属性值，最常用属性值：

|属性 | 描述| 默认  |
| -- | -- | -- |
| **language **| 指定JSP页面使用的脚本语言| java|
| **import **| 引用脚本语言中使用到的类文件 |无 |
| **contentType**| 指定JSP页面所采用的编码方方式|text/html<br>IOS-8859-1|

只有import指令可以重复设定，其余指令不可。

## include指令：
include指令表示在JSP编译时包含一个文本或者代码文件，这个包含过程是静态的，包含的文件可以是JSP网页，HTML网页，文本文件或者一段java代码

include只有一个属性file
语法：

```jsp
<%@ include file="被包含文件的地址" %>
```

## taglib指令
