---
layout: post
title: flask模板
category: Web
tags: [pythonweb,python,flask,flasktemplate]
keywords:
description:
---


## Flask-Moment

初始化Flask-Moment

```python
moment=Moment(app)
```

```python
/template/base.html
...
{% block scripts %}
{{ super() }}
{{ moment.include_moment() }}
{% endblock %}
```

```python
/templage/index.html
...
{# current_time是传入的 #}
{% block page_content %}
    <h1>{{ moment(current_time).format("dddd, MMMM Do YYYY, h:mm:ss a") }}</h1>
{% endblock %}
```
