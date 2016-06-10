---
layout: post
title: flask数据库
category: Web
tags: [pythonweb,python,flask,flaskdatabase]
keywords:
description:
---

![](/assets/img/posts/flask_database_url.png)

## 定义模型

```python
class Role(db.Model):
    __tablename__="roles"
    id=db.Column(db.Integer,primary_key=True)
    name=db.Column(db.String(61),unique=True)

    def __repr__(self):
        return "<Role %r>" % self.name

class User(db.Model):
    __tablename__="users"
    id=db.Column(db.Integer,primary_key=True)
    username=db.Column(db.String(64),unique=True,index=True)


    def __repr__(self):
        return "<User %r>" % self.username
```

`__tablename__`表示表明,一般使用复数. 没有定义`__tablename__`, flask-sqlchemy会使用一个默认名字
![](/assets/img/posts/flask_database_model-build.png)


## 关系
