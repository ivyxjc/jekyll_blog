---
layout: post
title: BeautifulSoup4入门
category: Python
tags: [python,spider,bs4]
keywords:
description:
---

## 对象的种类
Beautiful Soup会将HTML文档抓换成一个树形结构，每个节点都是Python对象，所有对象可以分为4类：`Tag`,`NavigableString`,`BeautifulSoup`,`Comment`。


### Tag
`Tag`与XML或HTML中的tag相同：

```python3
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>')
tag = soup.b
print(type(tag))
print(tag)

--<class 'bs4.element.Tag'>
--<b class="boldest">Extremely bold</b>
```

#### name

每一个 Tag都有自己的name，可以通过`.name`。改变tag的name，将会影响通过当前BS对象生成的HTML文档

```python3
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>',"html.parser")
tag = soup.b
print(tag)
print(tag.name)
tag.name="blockquote"
print(tag)

---<b class="boldest">Extremely bold</b>
---b
---<blockquote class="boldest">Extremely bold</blockquote>
```

#### attributes
一个tag可能有多个属性

```python3
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>',"html.parser")
tag = soup.b
print(tag['class'])
print(tag.attrs)

---['boldest']
---{'class': ['boldest']}
```

tag的属性可以被添加，删除或修改

```python
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>',"html.parser")
tag = soup.b
#更改属性
tag['class']="verybold"
tag['id']=1
print(tag)

#删除属性
del tag['class']
print(tag)
print(tag.get('class'))

---<b class="verybold" id="1">Extremely bold</b>
---<b id="1">Extremely bold</b>
---None