---
layout: post
title: bufferedreaderandprintwriter
category: 
tags: [javagitbook ]
keywords:
description:
---
# BufferedReaderAndPrintWriter
BufferedReader配合PrintWriter写读写文件<br>
但是PrintWriter无法更改charset，使用的是项目默认的charset

```java
    public static void main(String[] args)throws IOException{
        BufferedReader br=new BufferedReader(
                new InputStreamReader(
                        new FileInputStream("demo\\reader.dat")               )
        );

        BufferedWriter bw=new BufferedWriter(
                new OutputStreamWriter(
                        new FileOutputStream("demo\\writer.dat"),"utf-16be"
                )
        );

        String line;

        PrintWriter pw=new PrintWriter("demo\\writer.dat");
        while ((line=br.readLine())!=null){
            System.out.println(line);
    //        bw.write(line);
    //        bw.newLine();//不写这一句文件会不换行
    //        bw.flush();
            pw.println(line);
            pw.flush();
        }
        br.close();
        bw.close();
        pw.close();
    }
```