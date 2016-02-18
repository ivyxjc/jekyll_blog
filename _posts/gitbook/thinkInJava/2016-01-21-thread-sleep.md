---
layout: post
title: thread_sleep
category: 
tags: [javagitbook ]
keywords:
description:
---
# Sleep
```java

TimeUnit.MILLISECONDS.sleep(100);是较新的用法
```

```java
public class SleepingTask extends ListOff{
    @Override
    public void run() {
        super.run();
        try {
            System.out.println(status());
            TimeUnit.MILLISECONDS.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        } finally {
        }
    }

    public static void main(String[] args){
        ExecutorService exec= Executors.newCachedThreadPool();
        for(int i=0;i<5;i++){
            exec.execute(new SleepingTask());
        }
        exec.shutdown();
    }
}
```