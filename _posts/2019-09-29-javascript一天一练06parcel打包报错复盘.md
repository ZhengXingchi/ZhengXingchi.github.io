---
layout:     post
title:      "javascript一天一练06"
subtitle:   "parcel打包复盘"
date:       2019-09-29
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---


## postcss
`/demo/node_modules/antd/dist/antd.css:undefined:undefined: Parse error on line 1: 
384px - 16px 24px * 2 -...
-------------^
Expecting end of input, "RPAREN", "ADD", "SUB", "MUL", "DIV", got unexpected "LENGTH"`



总结观点如下：
1. antd版本好像@3.0.0版本有着问题，可以考虑将其升级为
```
"antd": {
    "version": "3.9.1",
    "resolved": "http://registry.npm.taobao.org/antd/download/antd-3.9.1.tgz",
    ...
}
```
其中有人说他有过相似的问题贴上
```
Btw I have the very same problem without having nested variables :

const postcssCalc = require('postcss-calc');

const css = `
.baz{
  height:calc( calc(16px + 0.8)+calc(1.5 + 0.9));
}
`

postcssCalc.process( css ).catch( error => console.error(error.toString()) );
This breaks with error :

JisonParserError: Parse error on line 1:
calc(16px + 0.8)2.4
----------------^
Expecting end of input, "ADD", "SUB", "MUL", "DIV", got unexpected "NUMBER"
I assume having nested calc with no space between breaks it, since

height:calc( calc(16px + 0.8)+ calc(1.5 + 0.9));
//                            ^ note space
works normally.
```


我在使用嵌套变量的时候出现类似问题，我寻思是因为嵌套的calc之间没有空格导致报错，修改以后就工作正常了。


2. 取消postcss关于calc的功能
在package.json中添加
```
  "cssnano": {
    "preset": [
      "default",
      {
        "calc": false
      }
    ]
  }
```


原话如下
```
As a workaround, disable postcss-calc in package.json to pass gatsby build in my case.

  "cssnano": {
    "preset": [
      "default",
      {
        "calc": false
      }
    ]
  }
Will enable again once this bug fixed. Thanks!
```


参考自[Parse error with CSS custom properties with default values including a nested calc #77](https://github.com/postcss/postcss-calc/issues/77)









