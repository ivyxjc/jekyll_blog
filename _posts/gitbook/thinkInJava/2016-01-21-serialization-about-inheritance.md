---
layout: post
title: serialization_about_inheritance
category: 
tags: [javagitbook ]
keywords:
description:
---
# 父子类的序列化

对子类对象进行反序列化操作，如果其父类没有实现Serializable接口<br>
那么其父类的**默认构造函数**会被调用。只会调用默认构造函数

若父类有实现Serializable接口,不会调用父类的构造函数。而是直接存储在序列化的字节之中


```java
/*
 一个类实现了序列化接口，那么它的子类就都能实现序列化
 */
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

...main()...{
        ObjectOutputStream oos2=new ObjectOutputStream(
                new FileOutputStream("demo\\obj1.dat")
        );

        Foo2 foo2=new Foo2();
        oos2.writeObject(foo2);
        oos2.flush();
        oos2.close();

        ObjectInputStream ois2=new ObjectInputStream(
                new FileInputStream("demo\\obj1.dat")
        );

        Foo2 foo2_2=(Foo2)ois2.readObject();
        ois2.close();
    }
out:
foo
foo111
foo222
```

调用父类构造函数是总是调用的是**默认构造函数**，所以反序列化得到的对象和原对象并不一定完全一样
```java
class Bar{
    public Bar(){
        System.out.println("bar");
    }
}

class Bar1 extends Bar{
    private int i=0;

    public Bar1(){
        System.out.println("bar--"+i+i+i);
    }

    public Bar1(int i){
        this.i=i;
        System.out.println(i);
    }
}
class Bar2 extends Bar1 implements Serializable{
    public Bar2(int i){
        super(i);
        System.out.println("bar222");
    }
}
...main()...{
ObjectOutputStream oos3=new ObjectOutputStream(
                new FileOutputStream("demo\\obj2.dat")
        );
        Bar2 bar2=new Bar2(4);
        oos3.writeObject(bar2);
        oos3.flush();
        oos3.close();

        ObjectInputStream ois3=new ObjectInputStream(
                new FileInputStream("demo\\obj2.dat")
        );
        Bar2 bar2_2=(Bar2)ois3.readObject();
        ois3.close();
        }
out:
bar
4
bar222
bar
bar--000

```