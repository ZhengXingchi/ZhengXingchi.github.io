---
layout:     post
title:      "javascript一天一练07"
subtitle:   "jquery的一点补充"
date:       2019-10-2
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---


## insertBefore before
在每个 p 元素之前插入 span 元素：与对象并列同级的位置插入内容
```
$("button").click(function(){
  $("<span>Hello world!</span>").insertBefore("p");
});

$("button").click(function(){
  $("<b>Hello World!</b>").before("p");
});
```

## insertAfter after
在每个 p 元素之后插入 span 元素

## append  appendTo
在每个 p 元素结尾插入内容：位于p元素内部
```
$("button").click(function(){
  $("p").append(" <b>Hello world!</b>");
});

$("button").click(function(){
  $("<b>Hello World!</b>").appendTo("p");
});
```

## preppend preppendTo
在每个 p 元素开头插入内容


## jq对象 > dom
jquery提供了两个方法可以实现jq对象转换为dom对象，即[index]和get(index)，因为jquery对象实际上是伪数组对象！

```
var $cr = $("#cr"); //jquery对象
var cr = $cr[0]; //dom对象，也可写成 var cr= $cr.get(0);
alert(cr.checked); //检测这个checkbox是否给选中
```

## dom对象 > jq对象
对于一个dom对象，只需要用$()把dom对象包装起来，就可以获得一个jquery对象了，方法为$(dom对象);
代码如下:
```
var cr = document.getElementById("cr"); //dom对象
var $cr = $(cr); //转换成jquery对象
```
















