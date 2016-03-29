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
---
```

##### 多值属性
多值属性即为可包含多个值的属性，最常见的即为`class`
`xml`中没有多值属性

多值属性的返回类型是list

```python
css_soup = BeautifulSoup('<p class="body strikeout"></p>',"html.parser")
print(css_soup.p['class'])

---['body', 'strikeout']
```

若某个属性看起来像多值属性，但是在任何版本HTML中都没有被定义为多值属性，那么BS会将这个属性作为字符串返回

```python
id_soup = BeautifulSoup('<p id="my id"></p>',"html.parser")
print(id_soup.p['id'])

---my id
```

### NavigableString

`NavigableString`不支持`.content`,`.string`,`find()`方法。

如果想在Beautiful Soup之外使用`NavigableString`对象,需要调用`unicode()`方法,将该对象转换成普通的Unicode字符串,否则就算Beautiful Soup已方法已经执行结束,该对象的输出也会带有对象的引用地址.这样会浪费内存.

```python
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>',"html.parser")
tag = soup.b
print(tag.string)
print(type(tag.string))
tag.string.replace_with("No long bold")
print(tag)

---Extremely bold
---<class 'bs4.element.NavigableString'>
---<b class="boldest">No long bold</b>
```

## BeautifulSoup

`BeautifulSoup`对象表示的是一个文档的全部内容.大部分时候,可以把它当作 Tag 对象,它支持 遍历文档树 和 搜索文档树 中描述的大部分的方法.

`BeautifuSoup`没有name和attribute属性。但有一个值为`[document]`的特殊属性`.name`

```python
soup = BeautifulSoup('<b class="boldest">Extremely bold</b>',"html.parser")
print(soup.name)

---[document]
```

### Comment

