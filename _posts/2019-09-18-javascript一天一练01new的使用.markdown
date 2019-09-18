---
layout:     post
title:      "javascript一天一练01"
subtitle:   "new的使用"
date:       2019-09-18
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---

```
function People(name) {
   this.name = name;
}
 People.prototype.sayName = function () {
   console.log(this.name);
}
var man1 = new People('xiaos');
console.log(man1.name)
man1.sayName();
```