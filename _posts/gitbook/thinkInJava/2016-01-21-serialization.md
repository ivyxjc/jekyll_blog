---
layout: post
title: serialization
category: 
tags: [javagitbook ]
keywords:
description:
---
# 序列化和反序列化


(1).对象序列化，就是将Object转换为byte序列，反之叫对象的反序列化<br>

(2).序列化流（**ObjectOutpputStream**),是过滤流--writeObject<br>
    反序列化流（**ObjectInputStream**)--readObject<br>

(3).序列化借口（**Serializable**)<br>
对象必须实现序列化借口，才能进行序列化，否则将出现异常<br>
该接口无任何方法，只是规定<br>
自己完成序列化**必须实现具有下面签名的方法**<br>
```java
 private void writeObject(java.io.ObjectOutputStream out)
     throws IOException
 private void readObject(java.io.ObjectInputStream in)
     throws IOException, ClassNotFoundException;
 private void readObjectNoData()
     throws ObjectStreamException;
```

对子类对象进行反序列化操作，如果其父类没有实现Serializable接口<br>
那么其父类的默认构造函数会被调用。只会调用默认构造函数

若父类有实现Serializable接口,不会调用父类的构造函数。而是直接存储在序列化的字节之中


