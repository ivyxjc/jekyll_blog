---
layout: post
title: fileinputstream
category: 
tags: [javagitbook ]
keywords:
description:
---
# FileInputStream

```java
public class IO_Input_Util{
    /*
    一个字节一个字节读取文件
    以字节的形式读取指定文件内容，按照16进制输出到控制台
    每输出10个字节就换行
     */
    public static void readHex(String fileName) throws IOException{
        //把文件作为字节流读操作
        FileInputStream in=new FileInputStream(fileName);

        int b;
        int i=0;
        while((b=in.read())!=-1) {
            if(b<=0xf){
                System.out.print("0"+Integer.toHexString(b)+" ");
            }
            else {
                System.out.print(Integer.toHexString(b) + " ");
            }
            i++;
            if (i % 10 == 0) {
                System.out.println();
            }
        }
        in.close();
    }

    //批量读取文件
    public static void readHexByByteArray(String fileName)throws IOException{
        FileInputStream in=new FileInputStream(fileName);

        byte[] buf=new byte[20*1024];
        /*从in中批量读取字节，放入到buf这个字节数组中，从第0个位置
        开始放，最多放buf.length个
        返回的是读到的字节的个数
         */
        int j=0;
        int bytes;


        while((bytes=in.read(buf,0,buf.length))!=-1){
            for(int i=0;i<bytes;i++){
                int tmp=(int)buf[i];//先将byte升到int
                tmp=tmp&0xff;//将前24位置0
                if(tmp<=0xf){
                    System.out.print("0");
                }
                System.out.print(Integer.toHexString(tmp)+" ");

                j++;
                if(j%10==0){
                    System.out.println();
                }
            }
        }
        in.close();
    }
}
```