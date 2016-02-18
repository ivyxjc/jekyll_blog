---
layout: post
title: thread_join
category: 
tags: [javagitbook ]
keywords:
description:
---
# Join

如果某线程在另一个线程t上调用t.join()，此线程将被挂起，直到t结束才会执行

t.join(time) 到time的话，join()方法总能返回

join()方法可以被中断，就是调用interrupt()方法

```java
class Sleeper extends Thread{
    private int duration;

    public Sleeper(String name,int sleepTime){
        super(name);
        duration=sleepTime;
        start();
    }

    @Override
    public void run() {
        super.run();
        try {
            sleep(duration);
        } catch (InterruptedException e) {
            System.out.println(getName()+" was interrupted. "+"isInterrupted(): "+isInterrupted());
            return;
        }
        System.out.println(getName()+" is awakened");
    }
}

class Joiner extends Thread{
    private Sleeper mSleeper;

    public Joiner(String name,Sleeper sleeper){
        super(name);
        mSleeper=sleeper;
        start();
    }

    @Override
    public void run() {
        super.run();
        try {
            mSleeper.join()
            //TimeUnit.MILLISECONDS.sleep(1000);
        } catch (InterruptedException e){
            System.out.println("Interrupted");
        }
        System.out.println(getName()+" join completed");
    }
}

public class Joining extends Thread{
    public static void main(String[] args){
        Sleeper sleepy=new Sleeper("Sleepy",2000);
        Sleeper grumpy=new Sleeper("Grumy",2000);

        Joiner dopey=new Joiner("Dopey",sleepy);
        Joiner doc=new Joiner("doc",grumpy);

        grumpy.interrupt();
    }

}
```


```java
out:
Grumy was interrupted. isInterrupted(): false
doc join completed          //等待1000毫秒后
Sleepy is awakened
Dopey join completed