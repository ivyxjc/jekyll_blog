---
layout: post
title: jsp_comment
category: 
tags: [javawebgitbook ]
keywords:
description:
---
# JSP注释

两类注释：<br>
&nbsp;&nbsp;&nbsp;&nbsp;HTML注释:<br>
&nbsp;&nbsp;&nbsp;&nbsp;隐藏注释（JSP专有注释）<br>

##HTML注释
HTML注释能在客户端代码中显示，且其中所有的脚本元素，指令和动作将正常执行。编译器会扫描注释内的内容
```html
<!--注释-->
```

```html
<!--This page is loaded at<% java.util.Date().toString() %>-->
会在客户端源码中显示
<!--This page is loaded at Tue Oct 26 11:11:44 CST 203 -->
```


##JSP注释

```jsp
<%--注释--%>客户端不可见
```


##JSP脚本注释

与java注释相同