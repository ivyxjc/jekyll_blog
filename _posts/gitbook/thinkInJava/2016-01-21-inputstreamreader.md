---
layout: post
title: inputstreamreader
category: 
tags: [javagitbook ]
keywords:
description:
---
# InputStreamReader

**InputStreamReader** 完成byte流解析成为char流，按照编码解析<br>
**OutputStreamWriter** 提供char流到byte流，按照编码处理

```java
public class IO_ReaderWrite_Util {
    public static void main(String[] args)throws IOException{
        InputStreamReader isr=new InputStreamReader(
            new FileInputStream("demo\\reader.dat"),"utf-8");//默认项目编码
        OutputStreamWriter osw =new OutputStreamWriter(
            new FileOutputStream("demo\\writer.dat"));

        char[] buffer =new char[8*1024];
        int c;
        //批量读取，放入buffer，从0开始放，最多放buffer.length
        while((c=isr.read(buffer,0,buffer.length))!=-1){
            osw.write(buffer,0,c);
            System.out.println(buffer);
        }
        
        isr.close();
        osw.close();

    }
}
```