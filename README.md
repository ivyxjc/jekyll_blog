##jekyll主题
该主题来自于[林安亚的博客](http://painterlin.com/), 在其基础上做了一定的修改。主要修改内容如下。<br>

##更改
1.```page/about.html```中删除了weibo，music等图标，仅保留了github，mailto和rss。<br>

2.增加了```Rakefile```文件，这样可以直接使用```rake title="filename"```自动在```_post```中创建md。<br>

3.增加了对Latex的支持,在```header.html```以及```header.html```中添加如下代码：<br>

```html
<script src='https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML'></script>
```

并在_config.yml中将markdown改为kramdown<br>

4.原博首页展示的是按tags来分的，我改为了按照categoris来分。代码[b497f73](https://github.com/ivyxjc/ivyxjc.github.io/commit/b0032df15246c81a695b4d6bf5f970bac14b3be8#diff-eacf331f0ffc35d4b482f1d15a887d3b)。


