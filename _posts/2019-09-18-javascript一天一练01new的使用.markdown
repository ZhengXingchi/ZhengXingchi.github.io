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

## 1.new的原理

```

   function People(name,age) {
     this.name = name;
     this.age=age;
    }
    People.prototype.sayName = function () {
      console.log(this.name);
    }
 
    var man1 = new People('Lise',18);
    console.log(man1.name)
    man1.sayName();
```

1. 创建一个空对象
`var obj={}`
2. 让Person中的this指向obj，并执行Person的函数体
`var result=Person.apply(obj,arguments)`
3. 设置原型链，将obj的__proto__成员指向了Person函数对象的prototype成员对象
`obj.__proto__ = Person.prototype;`
4. 判断Person的返回值类型，如果是值类型，返回obj。如果是引用类型，就返回这个引用类型的对象。
`
if (typeof(result) == "object")
    person = result; 
else
    person = obj;
`


## 2.设计函数实现原生new
```
function New () {
  let obj = new Object();
  let fn = [].shift.call(arguments);
  let args = arguments;
  var ret = fn.apply(obj, args);
  obj.__proto__ = fn.prototype;
  return typeof ret === 'object' ? ret : obj;
}

let person = New(Person, 'Bob', 23);
```