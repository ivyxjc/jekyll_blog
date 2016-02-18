---
layout: post
title: filereaderandwriter
category: 
tags: [javagitbook ]
keywords:
description:
---
# FileReaderAndWriter
封装好的读写工具，但是只能呢识别项目编码

```java
    public static void main(String[] args) throws IOException{
        //只能识别项目编码
        FileReader fr=new FileReader("demo\\reader.dat");
        FileWriter fw=new FileWriter("demo\\writer.dat");//true 就会追加内容

        char[] buffer=new char[1024];
        int c;
        while((c=fr.read(buffer,0,buffer.length))!=-1){
            fw.write(buffer,0,c);
            fw.flush();
        }
        fr.close();
        fw.close();
    }
}
```