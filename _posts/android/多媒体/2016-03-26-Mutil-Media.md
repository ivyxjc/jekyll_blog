---
layout: post
title: 跨程序共享数据
category: Android
tags: [android,androidfragment,fragment]
keywords:
description:
---

## 通知

```java
MainActivity.java

NotificationManager notificationManager=(NotificationManager)getSystemService(Context.NOTIFICATION_SERVICE);

Notification.Builder builder=new Notification.Builder(this);

//设置点击通知进入NotificationActivity
Intent intent=new Intent(this,NotificationActivity.class);

//第二个参数int requestCode相同，表示是同一个pendingIntent
PendingIntent pi=PendingIntent.getActivity(this,0,intent,PendingIntent.FLAG_CANCEL_CURRENT);

//设置通知栏 布局，内容等...
builder.setSmallIcon(R.mipmap.ic_launcher);
builder.setContentTitle("Notification Title");
builder.setContentText("Notification text");
builder.setContentIntent(pi);

//第一个参数在应用中是唯一的，代表这个通知
notificationManager.notify(11, builder.build());
```

 1.FLAG_CANCEL_CURRENT:如果当前系统中已经存在一个相同的PendingIntent对象，那么就将先将已有的PendingIntent取消，然后重新生成一个PendingIntent对象。
 2.FLAG_NO_CREATE:如果当前系统中不存在相同的PendingIntent对象，系统将不会创建该PendingIntent对象而是直接返回null。
 3.FLAG_ONE_SHOT:该PendingIntent只作用一次。在该PendingIntent对象通过send()方法触发过后，PendingIntent将自动调用cancel()进行销毁，那么如果你再调用send()方法的话，系统将会返回一个SendIntentException。
 4.FLAG_UPDATE_CURRENT:如果系统中有一个和你描述的PendingIntent对等的PendingInent，那么系统将使用该PendingIntent对象，但是会使用新的Intent来更新之前PendingIntent中的Intent对象数据，例如更新Intent中的Extras。


```java
NotificationActivity.java

NotificationManager manager=(NotificationManager)getSystemService(NOTIFICATION_SERVICE);

//使通知在通知栏消失
manager.cancel(11);
```

### 效果

![](assets/img/posts/notification.gif)
