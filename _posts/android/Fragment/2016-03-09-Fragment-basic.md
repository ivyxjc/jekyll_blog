---
layout: post
title: Fragment初步
category: Android
tags: [android,androidfragment,fragment]
keywords:
description:
---

## Fragment概要
![](assets/img/posts/fragmentIntro.png)

## **onCreateView()**方法

Fragment第一次绘制它的用户界面时，系统会调用此方法。为了方便绘制Fragment的UI，此方法必须返回一个View，如果不显示UI，返回null。


### 标识Fragment方法

android:id 提供一个唯一的ID 或
android:tag 提供一个唯一的字符串tag

## 静态加载

在**Activity**的layout文件中声明**Fragment**，其中**android:name**属性制定了在layout中实例化的Fragment类。

静态加载Fragment必须要给Fragment一个唯一的标识。

文件目录：
——src
————FragmentFirst.java (extends Fragment)
————MainActivity.java   (extends Activity)
————MainFirst.java	(extends Activity)

——layout
————fragment_container.xml
————fragment_first.xml
————main.xml
————main_first.xml

**FragmentFirst.java**利用**fragment_first.xml**返回一个**view**，**main_first.xml**中的**android:name="com.jc.fragmentbasic.FragmentFirst"**，然后**MainFirst**调用**setContentView(R.layout.main_first);**


### fragment_container.xml

```xml
<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.example.android_fragment.MainActivity"
    tools:ignore="MergeRootFrame" />
```


### main_first.xml

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">

    <fragment
        android:id="@+id/fragment_first"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:name="com.jc.fragmentbasic.FragmentFirst"/>

</LinearLayout>
```

### 加载过程的代码

```java
case R.id.first:{
    Intent intent=new Intent(this,MainFirst.class);
    startActivity(intent);
    break;
}
```

### 效果

![](assets/img/posts/fragment_first.gif)


## 动态加载

根据用户的交互情况，对Fragment进行添加，移除，替换，以及执行其他动作，提交Activity的每一套变化被称作一个**事务**。

每一事务都是同时执行一套变化，可以在一个事务中设置你所有执行的变化，包括add(),remove(),replace()，然后提交个Activity，必须调用commit()方法。

如果允许使用Back键返回前一Fragment的状态，调用commit()之前可以加入addToBackStack()方法。


### 加载过程代码

```java
case R.id.dynamic:{
    FragmentDynamic fragmentDynamic=new FragmentDynamic();
    FragmentManager fragmentManager=getFragmentManager();
    FragmentTransaction beginTransaction=fragmentManager.beginTransaction();
    beginTransaction.add(R.id.frame,fragmentDynamic);
    beginTransaction.commit();
    break;
}
```



