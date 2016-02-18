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

