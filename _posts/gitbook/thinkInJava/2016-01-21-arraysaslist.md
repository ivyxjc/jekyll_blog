---
layout: post
title: arraysaslist
category: 
tags: [javagitbook ]
keywords:
description:
---
# Arrays.asList()的一些问题
```java
class Snow{
    public String toString(){
        return "Snow";
    }
}
class Powder extends Snow{
    public String toString(){
        return "Powder";
    }
}
class Crusty extends Snow{
    public String toString(){
        return "Crusty";
    }
}
class Slush extends Snow{
    public String toString(){
        return "Slush";
    }
}
class Light extends Powder{
    public String toString(){
        return "Light";
    }
}
class Heavy extends Powder{
    public String toString(){
        return "Heavy";
    }
}

public class AsListInference {
    public static void main(String[] args){
        List<Snow> snow1= Arrays.asList(new Crusty(),new Slush(),new Powder());

        List<Snow> snow2=Arrays.asList(new Light(),new Heavy(),new Powder());//jdk8之前都不允许，必须使用下面的显示参数说明

        List<Snow> snow3=Arrays.<Snow>asList(new Light(),new Heavy(),new Powder());
        System.out.println(snow1);
        System.out.println(snow2);
        System.out.println(snow3);

    }
}


```

