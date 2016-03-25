---
layout: post
title: 数据持久化
category: Android
tags: [android,androidfragment,fragment]
keywords:
description:
---

## 数据存储到文件

`Context`类提供了一个`openFileOutput()`方法，可以将数据存储到指定的文件中。接受两个参数，
1. 第一个参数是文件名(无需包含路径)，默认存储 到`/data/data/<package name>/files/`目录下。
2. 第二个参数是文件的操作模式，主要有两种：`MODE_PRIVATE`和`MODE_APPEND`。其中`MODE_PRIVATE`是默认的操作模式，表示当指定同样文件名的时候，所写入的内容将会覆盖原文件中的内容。`MODE_APPEND`则表示如果该文件已存在就往文件里面追加内容。还有另外两种模式：`MODE_WORLD_READABLE`和`MODE_WORLD_WRITEABLE`表示允许其它的应用程序对该程序中的文件进行读写操作，已被废弃。

```java
public void save(String inputText){
    FileOutputStream out=null;
    BufferedWriter writer=null;
    try{
        out=openFileOutput("data", Context.MODE_PRIVATE);
        writer=new BufferedWriter(new OutputStreamWriter(out));
        writer.write(inputText);
    }catch (IOException e){
        e.printStackTrace();
    }finally {
        try{
            if(writer!=null){
                writer.close();
            }
        }catch (IOException e){
            e.printStackTrace();
        }
    }
}

public String load(){
    FileInputStream in=null;
    BufferedReader reader=null;
    StringBuilder content=new StringBuilder();

    try{
        in=openFileInput("data");
        reader=new BufferedReader(new InputStreamReader(in));
        String line="";
        while ((line=reader.readLine())!=null){
            content.append(line);
        }
    }catch (IOException e){
        e.printStackTrace();
    }finally {
        if(reader!=null){
            try{
                reader.close();
            }catch (IOException e){
                e.printStackTrace();
            }
        }
    }
    return content.toString();
}

```

## SharedPreferences存储

```java
//存储数据
SharedPreferences.Editor editor=getSharedPreferences("data",MODE_PRIVATE).edit();
editor.putString("name","Tom");
editor.putInt("age", 28);
editor.putBoolean("married", false);
editor.commit();

//读取数据

SharedPreferences preferences=getSharedPreferences("data",MODE_PRIVATE);
String name=preferences.getString("name", "");
boolean married=preferences.getBoolean("married", false);
int age=preferences.getInt("age",0);
```