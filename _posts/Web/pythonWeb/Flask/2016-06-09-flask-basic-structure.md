---
layout: post
title: 第一个flask程序
category: Web
tags: [pythonweb,python,flask]
keywords:
description:
---

第一完整的Flask例子

```python
from flask import Flask


app = Flask(__name__)


@app.route('/')
def hello_world():
    return 'Hello World!'

@app.route('/user/<name>')
def user(name):
    return '<h1>Hello, %s!</h1>' % name

if __name__ == '__main__':
    app.run()
```
从浏览器中访问`.../`会弹出Hello World!,访问`.../user/xx`,会弹出Hello,xx!.

## 请求-响应循环

### 程序和请求上下文

```python
@app.route('/')
def index():
    user_agent=request.headers.get("User-Agent")
    return '<p> Your browser is %s</p>' %user_agent
```

Flask使用*上下文*临时把某些对象变为全局访问.
在上面的例子中,我们将request在**一个线程**中全局可以访问.

Flask中的上下文分程序上下文和请求上下文
//todo

### 请求调度

### 请求钩子

### 响应
默认返回的`状态码`是200,但是可以自定义.

例:

```python
@app.route('/')
def index():
    return '<h1>Bad Request</h1>', 400
```

此例中返回的状态码便是400.

视图函数返回值可以接受三个参数,第三个参数是一个字典,可以添加到HTTP响应中.

Flask视图函数可以返回`Response`对象,`make_response`最多可以接受三个参数,与上述视图函数返回值相同.

还有一种特殊响应类型--`重定向`,会告诉浏览器一个新的地址用以加载新页面.

```python
return redirect(...)
```

还有一种特殊的响应由`abort`函数生成,一般用于处理错误.`abort`会把控制权交给Web服务器.

```python
abort(404)
```
