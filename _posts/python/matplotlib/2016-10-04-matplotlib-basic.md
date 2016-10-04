---
layout: post
title: matplot basic
category: Python
tags: [python,matplotlib]
keywords:
description:
---



## 2d散点图

```python
#设置颜色
colors = ['#0000FF','#3CB371']
#各点大小的list
sizeLab=np.add(sizeLab,20)
# print(sizeLab)

#设置横轴上下限
plt.xlim(0,25)

#设置横轴标号
# plt.xticks(np.linspace(0,15,5,endpoint=True))

#设置记号的标签
plt.xticks([2*np.pi, 4*np.pi, 0, np.pi/2, np.pi],
       [r'$2\pi$', r'$4\pi$', r'$0$', r'$\pi/2$', r'$\pi$'])

#设置横纵坐标label
plt.xlabel("x 轴label")
plt.ylabel("y 轴label")


plt.scatter(datingDataMat[:,1],datingDataMat[:,2],s=sizeLab, c=colors)
plt.show()
```





## 中文显示问题
