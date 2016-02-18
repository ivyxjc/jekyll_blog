---
layout: post
title: thread_itom
category: 
tags: [javagitbook ]
keywords:
description:
---
# 原子性

不要依赖操作的原子性来编写无锁的代码，看似安全实际上可能不安全。

原子性可应用于**除longs和double**之外的所有基本类型的“简单操作”。对于读取和写入除long和double之外的基本类型变量这样的操作，可以保证他们会被当作不可分（原子）的操作来操作内存。<br>
64位的long和double会分成两个32位独立操作，会出现字撕裂。

当使用long和double时，加上**volatile**会获得简单操作的原子性。

多处理器系统中，可视性比原子性可能更为重要。即使在不中断的意义上是原子性的，对其它任务可能是不可视的（etc.修改只是暂时性地存储在本地处理器的缓存中）。

同步会强制在多处理器系统中，一个任务做出的修改必须在应用中可视。

**注：java的++，--操作并不是原子性操作，且volatile不能对++，--操作不是原子性操作产生影响**

##volatile
**volatile**确保了可视性。<br>
一个域被声明为volatile，那么只要对这个域产生了写操作，那么所有的读操作就能可以看到这个更改。即使使用本地缓存，也会立刻写入主存。<br>
在非volatile域上的原子操作不必刷新到主存中区，因此其它任务可能看不见这个新值。

###应用情况
多个任务同时访问某个域，这个域就应该是volatile。否则这个域只能经由同步来访问，同步也会导致向主存刷新。如果一个域完全由synchronized方法或语句块防护，那就不必设置为volatile。<br>
一个任务所作的任何写入操作对这个任务来说都是可视的，因此如果它只需要在这个任务内部可视，那么就不需要将其设置为volatile。
当一个域的值依赖于之前的值或者一个域的值受另外域的值限制，volatile将无法工作。

**第一选择仍应使用sychronized**。

```java
public class AtomicityTest implements Runnable {
    private int i=0;

    public int getValue(){
        return i;
    }

    private synchronized void evenIncrement(){
        i++;
        i++;
    }

    @Override
    public void run() {
        while (true)
        {
            evenIncrement();
        }

    }

    public static void main(String[] args){
        ExecutorService exec= Executors.newCachedThreadPool();
        AtomicityTest at=new AtomicityTest();
        exec.execute(at);
        while(true){
            int val=at.getValue();
            if(val%2!=0){
                System.out.println(val);
                System.exit(0);
            }
        }
    }
}
```
该段代码仍然会找到奇数值而退出。**虽然return i是原子性操作，但缺少同步使得其数值可以在处于不稳定的中间状态时被读取。<br>
此外，由于volatile不是volatile的，因此还存在可视性问题**。

改为如下就没有问题：
```java
public synchronized int getValue(){
    return i;
}
```









