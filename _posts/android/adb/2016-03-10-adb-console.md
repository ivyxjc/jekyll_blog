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

**adb -s &lt; serial number &gt; shell** :serial number及上命令得到的设备编号

## 录制屏幕相关
**adb screerecord /sdcard/test.mp4**：录制手机实况视频到test.mp4，按**ctrl+c**结束，否则录制320s。

**adb screerecord --size 1280*720 /sdcard/test.mp4** :制定视频大小

** adb shell screenrecord --bit-rate 6000000 /sdcard/test.mp4** :制定视频码率

**adb shell screenrecord --rotate /sdcard/test.mp4** :旋转

**adb pull /sdcard/test.mp4 E:/** :导出视频
