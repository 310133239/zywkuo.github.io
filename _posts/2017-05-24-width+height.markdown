---
layout:     post
title:      "js和jq获取当前位置"
subtitle:   "js原生判断点钱位置和jq判断当前位置"
date:       2017-05-24
author:     "zyw"
header-img: "img/2017-05-24/post-bg-js-version.jpg"
navcolor:   "invert"
header-mask: 0.3
catalog:    true
tags:
    - js和jq判断位置
    - js和jq判断位置
---

在写javascript的时候，有的时候需要判断盒子的当前位置，或者鼠标位置，在这里我就总结一下这些判断方法，先来一张直观图。
![](/img/2017-05-24/wh.gif)
```javascript
javascript原生写法
BODY对象宽度：document.body.clientWidth
BODY对象高度：document.body.clientHeight
可见区域宽度：document.documentElement.clientWidth
可见区域高度：document.documentElement.clientHeight
网页可见区域宽：document.body.offsetWidth (包括边线的宽)
网页可见区域高：document.body.offsetHeight (包括边线的高)
网页正文全文宽：document.body.scrollWidth
网页正文全文高：document.body.scrollHeight
网页被卷去的高：document.body.scrollTop
网页被卷去的左：document.body.scrollLeft
网页正文部分上：window.screenTop
网页正文部分左：window.screenLeft
屏幕分辨率的高：window.screen.height
屏幕分辨率的宽：window.screen.width
屏幕可用工作区高度：window.screen.availHeight
屏幕可用工作区宽度：window.screen.availWidth
获取元素的宽度：obj.clientWidth
元素的高度：obj.clientHeight
偏移坐标left：obj.offsetLeft
偏移坐标top：obj.offsetTop
元素的宽度：obj.offsetWidth
元素的高度：obj.offsetHeight
```

```javascript
jquery写法
偏移坐标left：$(selector).offset().left
偏移坐标top：$(selector).offset().top
宽度：$(w).height() //可试区域w=window、页面的文档w=documene、元素w=obj
高度：$(h).width(); //可试区域h=window、页面的文档h=documene、元素h=obj
滚动高度：$(document).scrollTop()
滚动宽度：$(document).scrollTop()
```

```javascript
js原生+jquery写法
偏移坐标left：$(selector)[0].offsetLeft
偏移坐标top：$(selector)[0].offsetTop
```

> 先这么多，持续更新。。。。。。