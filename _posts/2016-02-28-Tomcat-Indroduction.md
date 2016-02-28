---
layout: post
title: Tomcat介绍与简单应用
category: Web
tags: [tomcat,javaweb]
keywords:
description:
---
## Tomcat\webapps\mywebapp\文件目录
有文件夹**WEB-INF**以及index.jsp(默认的主页)。

## Tomcat\webapps\mywebapp\WEB-INF\文件目录
**WEB-INF**文件夹内有**clases**(存放**.class**文件)和**lib**(存放依赖的jar包)文件夹。以及配置文件**web.xml**。


```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
  version="4.0"
  metadata-complete="true">
<!-- 更改默认的欢迎页面为haha.jsp -->
  <welcome-file-list>
    <welcome-file>/haha.jsp</welcome-file>
  </welcome-file-list>
</web-app>
```



