---
layout: post
title: flask表单
category: Web
tags: [pythonweb,python,flask,flaskform]
keywords:
description:
---


## 表单类

```python
class NameForm(Form):
    name=StringField("What is your name?",validators=[DataRequired()])
    submit=SubmitField("Submit")
```
这个表单中有一个名为`name`的文本字段和名为`submit`的提交按钮
StringField
类表示属性为type="text" 的&lt;input&gt;元素。 SubmitField 类表示属性为type="submit" 的&lt;input&gt; 元素。

StringField 构造函数中可选参数validators指定一个由验证函数组成的列表,在接受用户提交数据之前验证数据.验证函数`DataRequired()`确保数据不为空

![](/assets/img/posts/flask_form.png)

```python
@app.route('/',methods=['GET','POST'])
def index():
    name=None
    form=NameForm()
    if form.validate_on_submit():
        name=form.name.data
        form.name.data=""
    return render_template('index.html',current_time=datetime.utcnow(),form=form,name=name)
```
提交数据后如果能被所有的验证函数接受,则`validate_on_submit()`返回True,否则返回False.
