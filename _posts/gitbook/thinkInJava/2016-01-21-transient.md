---
layout: post
title: transient
category: 
tags: [javagitbook ]
keywords:
description:
---
# transient

自己完成序列化**必须实现具有下面签名的方法**<br>
```java
 private void writeObject(java.io.ObjectOutputStream out)
     throws IOException
 private void readObject(java.io.ObjectInputStream in)
     throws IOException, ClassNotFoundException;
 private void readObjectNoData()
     throws ObjectStreamException;
```

```java
class Student implements Serializable{
    private String name;
    private int number;
    private transient int age;//transient会使得该元素不会被jvm序列化

    private void writeObject(java.io.ObjectOutputStream s)throws java.io.IOException{
        s.defaultWriteObject();//把jvm能默认序列化的操作自己完成序列化
        s.writeInt(age);//自己完成序列化
    }

    private void readObject(java.io.ObjectInputStream s)
            throws java.io.IOException, ClassNotFoundException{
        s.defaultReadObject();//把jvm能默认反序列化的元素进行反序列化得操作
        this.age=s.readInt();//自己完成age的反序列化
    }

    public Student(){

    }

    public Student(String name, int number, int age) {
        this.name = name;
        this.number = number;
        this.age = age;
    }
    @Override
    public String toString() {
        return name+number+age;
    }
}

 public static void main(String[] args)throws Exception {
        String file = "demo\\obj.dat";
        //1.对象的序列化
        ObjectOutputStream oos=new ObjectOutputStream(new FileOutputStream(file));
        Student stu=new Student("张三",100,20);
        oos.writeObject(stu);
        oos.flush();
        oos.close();
        //对象的反序列化
        ObjectInputStream ois=new ObjectInputStream(new FileInputStream(file));
        Student stu2=(Student)ois.readObject();
        System.out.println(stu2);
        ois.close();
        }
        
out:
张三10020
```
