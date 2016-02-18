---
layout: post
title: arraylist
category: 
tags: [javagitbook ]
keywords:
description:
---
# ArrayList

##ArrayList在java api中的结构
```
java.lang.Object
   java.util.AbstractCollection<E>
     java.util.AbstractList<E>
       java.util.ArrayList<E>
     
All Implemented Interfaces:
Serializable, Cloneable, Iterable<E>, Collection<E>, List<E>, RandomAccess

Direct Known Subclasses:
AttributeList, RoleList, RoleUnresolvedList
```
##最基本的方法

使用add()插入对象<br>
使用get()访问对象<br>
size()获取对象数量<br>

```java
//java
//without generic
//未使用泛型
class Apple{
	private static long counter;
	private final long id=counter++;
	public long id(){
		return id;
	}
}
class Orange{}
public class ApplesAndOrangesWithoutGenerics {
	//@SuppressWarnings("unchecked")
	public static void main(String args[]){
		ArrayList apples=new ArrayList();
		for(int i=0;i<3;i++){
			apples.add(new Apple());
		}
		apples.add(new Orange());	
		for(int i=0;i<apples.size();i++){
			long tmp=((Apple)apples.get(i)).id();
//在执行id()之前，需执行向上转型（(Apple)). 
//若apples之前添加了orange，此时会发生运行时错误
			System.out.println(tmp);		
		}	
	}
}
```
```java
ArrayList<Apple> apples=new ArrayList<>;//使用泛型，无法将Orange加入apples。会发生编译错误。可以将Apple的子类放入apples中。
```





