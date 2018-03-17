---
layout: post
title: centos7各种配置
category: Linux
tags: [linux]
keywords: centos7
description:
---


# 环境配置

## 更改ssh端口以及防火墙开放端口
[怎样修改 CentOS 7 SSH 端口](https://sebastianblade.com/how-to-modify-ssh-port-in-centos7/)([archive存档](https://web.archive.org/web/20180317035653/https://sebastianblade.com/how-to-modify-ssh-port-in-centos7/))


## 安装Java
直接wget下载地址并不能成功下载。使用下面的方式可以成功下载jdk-8u162.rpm.
使用`rpm -qa | grep 'jdk'`查找已安装的jdk，使用`rpm -e jdk**`来删除。之后使用`rpm -ivh jdk**`来安装新的jdk.

```
wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u162-b12/0da788060d494f5095bf8624735fa2f1/jdk-8u162-linux-x64.rpm?AuthParam=1521257408_9aefdf6daa3472d09007c0abd24832e1"
```

## 安装MySql

### 安装

[Centos 7 安装 MySQL](https://www.jianshu.com/p/7cccdaa2d177)([google cache](https://webcache.googleusercontent.com/search?q=cache:E4urk8c-wMYJ:https://www.jianshu.com/p/7cccdaa2d177+&cd=1&hl=zh-CN&ct=clnk&gl=cn))

### 允许外网访问
1. 云服务安全组及系统防火墙放开该端口
2. 进入`mysql`执行`grant all privileges on *.* to root@% identified by '1';`即可外网访问且拥有全部权限。


## 安装docker
`uname -r`检查内核版本号是否大于`3.10`

`yum -y install docker`安装docker

# 问题解决

## enable ipv4_forwarding
在 `/etc/sysctl.conf`以及 `/usr/lib/sysctl.d/50-default.conf`里面都添加`net.ipv4.ip_forward = 1 `

