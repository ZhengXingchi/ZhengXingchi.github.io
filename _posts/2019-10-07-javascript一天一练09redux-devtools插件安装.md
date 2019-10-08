---
layout:     post
title:      "javascript一天一练09"
subtitle:   "redux-devtools插件"
date:       2019-10-7
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---


##  1.首先打开官网：https://github.com/zalmoxisus/redux-devtools-extension


## 2. zip包

[zalmoxisus/redux-devtools-extension](https://github.com/zalmoxisus/redux-devtools-extension/releases)




## 坑
#### 1. primordials is not defined in node
参考[How to fix ReferenceError: primordials is not defined in node](https://stackoverflow.com/questions/55921442/how-to-fix-referenceerror-primordials-is-not-defined-in-node)

Solution: Either upgrade to gulp 4 or downgrade to an earlier node.
有两种解决方案要么降低node的版本要么把gulp从v3升级到v4

```
npm install -g n
sudo n 11.15.0
```

但是gulp升级以后会伴随其他错误，详见gulpv3与v4写法的不同[How do I update to Gulp 4?](https://www.liquidlight.co.uk/blog/how-do-i-update-to-gulp-4/)

















