---
layout: post
title: char_stream
category: 
tags: [javagitbook ]
keywords:
description:
---
# 字符流

字符流
(1)编码问题

(2)认识文本和文本文件
java的文本(char)是16位无符号证书，是字符的Unicode编码（双字节编码<br>）
文件是byte byte byte ...的数据序列<br>
文本文件时文本(char)序列按照某种编码方案(utf-8,utf-16be,gbk...)序列化为byte的文件<br>

(3)字符流(Reader Writer)<br>
字符的处理，一次处理一个字符<br>
字符的底层仍然是基本的字节序列<br>
字符流的基本实现<br>

