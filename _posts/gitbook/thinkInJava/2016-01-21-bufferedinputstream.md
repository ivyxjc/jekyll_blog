---
layout: post
title: bufferedinputstream
category: 
tags: [javagitbook ]
keywords:
description:
---
# BufferedInputStream

```java
    /**
     * 进行文件的拷贝，利用带缓冲的字节流
     * @param:srcFile
     * @param:destFile
     * @throws java.io.IOException
     */
    public static void copyFileByBuffer(File srcFile,File destFile)throws IOException{

        if(!srcFile.exists()){
            throw new FileNotFoundException(srcFile+"is not found");
        }

        if(!srcFile.isFile()){
            throw new IllegalArgumentException(srcFile+" is not a file");
        }

        BufferedInputStream bis =new BufferedInputStream(new FileInputStream(srcFile),20*1024);
        //可以设置缓冲区大小

        BufferedOutputStream bos =new BufferedOutputStream(new FileOutputStream(destFile),20*1024);

        int c=0;
        while((c=bis.read())!=-1){
            bos.write(c);
            //bos.flush();//刷新缓冲区
        }
        bis.close();
        bos.close();
    }
    ```