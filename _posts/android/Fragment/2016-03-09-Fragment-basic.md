---
layout: post
title: Fragment初步
category: Android
tags: [android,androidfragment,fragment]
keywords:
description:
---

## Fragment
![](assets/img/posts/fragmentIntro.png)

### ```onCreateView()```方法

Fragment第一次绘制它的用户界面时，系统会调用此方法。为了方便绘制Fragment的UI，此方法必须返回一个View，如果不显示UI，返回null。
