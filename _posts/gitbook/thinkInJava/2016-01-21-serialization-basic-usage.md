---
layout: post
title: serialization_basic_usage
category: 
tags: [javagitbook ]
keywords:
description:
---
# [基本使用]

```java
class Foo implements Serializable{
    public Foo(){
        System.out.println("foo");
    }
}

class Foo1 extends Foo{
    public Foo1(){
        System.out.println("foo111");
    }
}

class Foo2 extends Foo1{
    public Foo2(){
        System.out.println("foo222");
    }
}
```