---
layout: post
title: 部署jekyll博客
category: Web
tags: []
keywords:
description:
---
第一次部署jekyll博客，也折腾了好一会。

# 创建

```clone```代码下来，更改```_config.yml```及其它地方的一些内容。详见[Github](https://github.com/ivyxjc/ivyxjc.github.io)的```REAAME.md```。


# 博客的结构

```Categories```主要有```java```，```android```，```web```,随笔等几类，在博客左边栏中可以查看到。<br>
分类中不会看到*GitBook*中的内容，详见下方说明。<br>

```tags```都为小写。<br>

# 博客所使用的一些服务

 1. 最下方绑定了Disqus的评论系统<br>
 2. 使用了Google Analystic
 3. 使用CloudFlare的SSL。(In progress)

## GitBook内容的处理
写了一个小程序来使*GitBook*中的内容符合jekyll的格式要求。<br>
将*GitBook*中之前写的一些内容直接移入，可以从左侧```GitBook```按钮点击进入。中栏中会显示书名，点击书名后正文会显示```Summary.md```的内容(即目录)。<br>

# Attention
博客文本内容 在每一个属性之后必须有一个空格，否则无法识别。