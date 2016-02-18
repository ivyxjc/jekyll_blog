---
layout: post
title: byte_stream
category: 
tags: [javagitbook ]
keywords:
description:
---
# 字节流

1.字节流<br>
(1)** InputStream OutputStream**  都是抽象类<br>
InputStream抽象了应用程序读取数据的方式<br>
OutputStream抽象了应用程序写出数据的方式<br>

(2)EOF=End 读到-1就读到结尾<br>

(3)输入流基本方法<br>
int b=in.read();读取一个字节无符号填充到int低8位，-1是EOF<br>
in.read(byte[] buf)<br>
in.read(byte[] buf,int start,int size)<br>

(4)输出流基本方法<br>
out.write(int b)写出byte到流，b的低8位<br>
out.write(byte[] buf)将buf字节数组都写入流<br>
out.write(byte[] buf,int start,int size)从start开始，size的内容写入流<br>

(5)FileInputStream<br>
实现了文件上的读取

| 类| 功能 |构造器参数 |
| -- | -- | -- |
| **ByteArrayInputStream** | 允许将内存的缓冲区<br>作为InputStream使用 ||
| **StringBufferInputStream** |将String转换为InputStream |  |
| **FileInputStream** |用于从文件读取信息 |  |
| **PipedInputStream** |实现“管道化”的概念 |  |
| **SequenceInputStream** | 将多个InputStream<br>转变为一个InputStream ||
| **FilterInuptStream **|抽象类，作为装饰器的接口  |  |

| 类| 功能 |构造器参数 |
| -- | -- | -- |
| **ByteArrayOutputStream** | 在内存中创建缓冲区<br>所有送往流的数据都要放在此缓冲区中|  |
|**FileOutputStream** |用于将信息写至文件 |  |
| **PipedInputStream** |  |  |
|**FilterOutputStream**|     |    |



