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

## 遍历文档树

```
html_doc = """
<html><head><title>The Dormouse's story</title></head>

<p class="title"><b>The Dormouse's story</b></p>

<p class="story">Once upon a time there were three little sisters; and their names were
<a href="http://example.com/elsie" class="sister" id="link1">Elsie</a>,
<a href="http://example.com/lacie" class="sister" id="link2">Lacie</a> and
<a href="http://example.com/tillie" class="sister" id="link3">Tillie</a>;
and they lived at the bottom of a well.</p>

<p class="story">...</p>
"""
```

### `.content`和`.children`
tag的`.contents`属性可以将tag的子节点以列表的方式输出:
通过tag的`.children`生成器,可以对tag的子节点进行循环:

```python
print(soup.title.contents)
print(soup.title.contents[0])

---["The Dormouse's story"]
---The Dormouse's story
```

```python
for i in soup.head.children:
    print(i)

---<title>The Dormouse's story</title>
```

### `.descendants`

`.descendants`属性可以对所有tag的子孙节点进行递归循环

```python
print(soup.head.contents)
for child in soup.head.descendants:
    print(child)

print(len(list(soup.children)))
print(len(list(soup.descendants)))

---[<title>The Dormouse's story</title>]
---<title>The Dormouse's story</title>
---The Dormouse's story
---2
---25
```

### `.string`

如果tag只有一个`NavigableString`类型子节点,那么这个tag可以使用`.string`得到子节点

```python
print(soup.head.string)

---The Dormouse's story
```

### `.strings`和`stripped_strings`
如果tag中有多个字符串，可以使用`.strings`循环获取
使用`.stripped_strings`可以去除多余空白内容：

```python
for string in soup.stripped_strings:
    print(repr(string))
```


