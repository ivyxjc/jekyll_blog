---
layout: post
title: 
category: OJ
tags: [格式化输出,onlinejudge]
keywords:
description:
---

[题目网址](http://codeforces.com/contest/622/)
## A:Infinite Sequence


A题比较简单,主要就利用公式$$\sum_{k=1}^n k=\frac {(1+n)*n}{2}$$来确定距离所要求的数字最近的一个1所在的位置。然后就可得到该数值了。
代码如下
```java
public class Round7_A{
        public static void main(String[] args){
            Scanner in=new Scanner(System.in);
            long  a=in.nextLong();
            long a_one=count(a);

            if(a_one*a_one+a_one==2*a){
                System.out.println(a_one);
            }else{
                long tmp=(long)a-(a_one*a_one+a_one)/2;
                System.out.println(tmp);
            }
            return;
        }

        public static long count(long  num) {
            long num_two = 2 * num;
            long i = (long) Math.sqrt(num_two) - 1;
            //System.out.println(i);
            if (i <= 0) {
                i = 0;
            }
            for (; i <= num; i++) {
                //System.out.println(i);
                if (i * i + i == num_two) {
                    return i;
                }
                if (i * i + i > num_two) {
                    return i - 1;
                }
            }
            return 0;
        }
}
```

## B. The Time
B题也比较简单，主要就注意几个边界条件即可以及格式化输出即可。

```java
//num只有个位时，会自动在十位补0
DecimalFormat df=new DecimalFormat("00");
df.format(num);
```


## C. Not Equal on a Segment

题意为查询一个数组的某一区间与指定的x不相同的




