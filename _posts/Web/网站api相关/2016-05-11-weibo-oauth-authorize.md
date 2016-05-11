---
layout: post
title: 微博Oauth授权s
category: Web
tags: [weibo]
keywords:
description:
---

## 第一步
```python
url="https://api.weibo.com/oauth2/authorize?client_id="+cilent_id+"&response_type=code&redirect_uri="+redirect_uri
```

使用`GET`方式访问上述网址:
1.`cilent_id`: `app_key`
2.`redirect_uri`填写的授权回调页面
## 第二步

访问上述网址后,若授权成功,会自动跳转到一个页面,将网址最后的`code=`内容记录下来为`code`

## 第三步

这一步很烦,按照官方的文档试了半天都没用,原因很奇葩.

官方文档要求用`POST`访问`https://api.weibo.com/oauth2/access_token`, 参数为'cilent_id','cilent_secret'....

事实上这么做没用,结果得到的是 'error 21323','miss cilent id or cilent secret'


正确做法:

```python
url="https://api.weibo.com/oauth2/access_token?client_id="+cilent_id+"&client_secret="+cilent_secret+"&grant_type=authorization_code&redirect_uri="+redirect_uri+"&code="+code
```

但是仍需要使用`POST`提交,这是会就会返回`Access Token`.
