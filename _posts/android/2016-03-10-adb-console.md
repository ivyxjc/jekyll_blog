---
layout: post
title: adb常用命令
category: Android
tags: [android,adb]
keywords:
description:
---

## 设备相关
**adb devices**:查看连接的设备<br>

**adb -s &lt serial number &gt shell** :serial number及上命令得到的设备编号

## 录制屏幕相关
**adb screerecord /sdcard/test.mp4**：录制手机实况视频到test.mp4，按**ctrl+c**结束，否则录制320s。

