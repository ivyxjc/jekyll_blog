---
layout: post
title: executorservice
category: 
tags: [javagitbook ]
keywords:
description:
---
# ExecutorService

```java
        //合理的Executor首选，出问题是选择newFixedThreadPoll(int nThreads)
        ExecutorService exec= Executors.newCachedThreadPool();

        //预先执行线程分配，限制线程数量
        //ExecutorService exec=Executors.newFixedThreadPool(2);

        for(int i=0;i<5;i++){
            exec.execute(new ListOff());
        }
        //shutdown()会防止有新任务提交给该Executor
        //但仍会执行在调用shutdown()之前所提交的任务
        //该Executor会砸所有任务完成之后尽快退出

        /*The shutdown() method will allow previously submitted tasks
        to execute before terminating,
        while the shutdownNow() method prevents waiting tasks from starting
        and attempts to stop currently executing tasks
         */
        exec.shutdown();
        ```