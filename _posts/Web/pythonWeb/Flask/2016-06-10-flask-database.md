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

```python
class Role(db.Model):
    __tablename__="roles"
# ...
    users = db.relationship('User', backref='role')
class User(db.Model):
    __tablename__="users"
# ...
    role_id = db.Column(db.Integer, db.ForeignKey('roles.id'))
```

使用`users`表中的外键连接了两行. `role_id`被定义为外键.与`roles.id`建立联系.

`Role`模型中的`users`属性代表这个关系的面向对象视角.对于一个`Role`类的实现, `users`属性将返回与角色相关联的用户组成的列表. `db.relationship()`第一参数表明这个关系的另一端是哪个模型. `backref`参数项`User`模型中添加以个`role`属性, 从而定义反向关系.这一属性可代替`role_id`访问`Role`模型,获取的是模型对象而不是外键的值.

## 数据库操作

![](/assets/img/posts/flask_filter.png)

## 数据库迁移

需要安装`Flask-Migrate`


## 效率


### 如何连接mysql数据库

由于`python-mysql`目前并不支持python3.5，所以使用`pymysql`库。

```python
mysql_uri='mysql+pymysql://username:password@localhost/database'

app.config['SQLALCHEMY_DATABASE_URI']=mysql_uri
db=SQLAlchemy(app)
```

### 如何进行模糊查询
