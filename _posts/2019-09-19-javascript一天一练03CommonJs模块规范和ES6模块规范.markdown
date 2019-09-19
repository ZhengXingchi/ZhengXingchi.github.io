---
layout:     post
title:      "javascript一天一练03"
subtitle:   "CommonJs模块规范和ES6模块规范"
date:       2019-09-19
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---


## CommonJs模块规范
#### 1. exports、module.exports的区别
`module`和`exports`是`Node.js`给每个js文件内置的两个对象。可以通过`console.log(module)`和`console.log(exports)`打印出来。如果你在`main.js`中写入下面两行，然后运行`$ node main.js`:

```
console.log(exports);//输出：{}
console.log(module);//输出：Module {..., exports: {}, ...} （注：...代表省略了其他一些属性）
```

从打印我们可以看出，`module.exports`和`exports`一开始都是一个空对象{}，实际上，这两个对象指向同一块内存。这也就是说`module.exports`和`exports`是等价的（有个前提：不去改变它们指向的内存地址）。

例如：`exports.age = 18`和`module.export.age = 18`，这两种写法是一致的（都相当于给最初的空对象{}添加了一个属性，通过require得到的就是`{age: 18}`）。

但是
require引入的对象本质上是`module.exports`。这就产生了一个问题，当 `module.exports`和`exports`指向的不是同一块内存时，`exports`的内容就会失效。
例如：
```
module.exports = {name: '萤火虫叔叔'}；
exports = {name: '萤火虫老阿姨'}
```

此时`module.exports`指向了一块新的内存（该内存的内容为`{name: '萤火虫叔叔'}`），`exports`指向了另一块新的内存（该内存的内容为`{name: '萤火虫老阿姨'}`）。require得到的是`{name: '萤火虫叔叔'}`。
 
 附上代码（在main.js中引入people.js）

```
 //people.js
module.exports = {name: '萤火虫叔叔'}；
exports = {name: '萤火虫老阿姨'};
```

```
//main.js
let people = require('./people');
console.log(people);//输出：{name: '萤火虫叔叔'}
```

#### 2. 在node.js中，如果引入模块直接通过require方式引入，问题是这种方式其实是在运行时加载相应模块整体，哪怕前面只引用了其中一个方法
```
const {join,basename} = require ('path');  
/*require后的路径如果为/开头，为绝对路径 ./为相对路径
 字符串表示为node核心模块，已经局部安装或者全局安装*/
//运行时相当于
const _path = require('path');  //将整个path模块赋给_path对象
const join = _path.join;
const basename = _path.basename;
```
因为这个对象只在程序运行时才加载生成新对象，这种加载被称为“运行时加载”，没办法再编译时做静态优化。

## es6模块规范
新建两个文件：a.js, b.js。a.js用于导出模块，b.js用户导入模块。两个文件放在同一目录下。
#### 1. export default导出
```
//a.js
const Programmer = {name: 'UncleFirefly',age:25}
export default Programmer
```

export default导出对应的导入：

```
//b.js
import Programmer from './a.js'
```

#### 2. export导出
```
//a.js
const uncle = {name: 'UncleFirefly',age:25}
const aunt = {name: 'AuntFirefly',age:25}
export {uncle, aunt}
```
export default导出对应的导入：
```
//b.js
import {uncle, aunt} from './a.js'
```


#### 3. export和export default的区别
```
//a.js
const Programmer = {name: 'UncleFirefly',age:25}
export default Programmer
console.log(module)
/*
//打印结果
{exports: {default:{age:25,name:'UncleFirefly'}, hot:{...}}
*/
```

```
//a.js
const uncle = {name: 'UncleFirefly',age:25}
const aunt = {name: 'AuntFirefly',age:25}
export {uncle, aunt}
/*
//打印结果
{exports: {aunt:{age:25,name:'AuntFirefly'},uncle:{age:25,name:'UncleFirefly'}, hot:{...}}
*/
```

从打印可以看出:

- 导出时
  - export相当于把对象添加到module的exports中。
  - export default相当于把对象添加到module的exports中，并且对象的key叫default。

- 导入时：
  - 不带{}的导入
本质上就是导入exports中的default属性（注：如果default属性不存在，则导入exports对象）。

  - 带{}的导入
本质上按照属性key值导入exports中对应的属性值。

#### 4. 其他
值得一提的是ES6模块的设计思想是尽量的静态化，使得编译时就能确定模块的依赖关系，以及输入和输出的变量。所以import在编译时就已经运行，它也就具有了声明提升效果。
export命令规定的是对外的接口，必须与模块内部的变量建立一一对应关系，不能直接输出常量。
在一个文件或模块中，export、import可以有多个，export default仅有一个。

export写法
```
export let a=1;
//或者
let a=1;
export {a}
export{a as b}
```

import写法
```
//export输出
import {a,b,c} from './a.js';
//export default输出
import a from './a.js
```
 另外，export语句输出的接口，与其对应的值是动态绑定关系，即通过该接口，可以取到模块内部实时的值。







