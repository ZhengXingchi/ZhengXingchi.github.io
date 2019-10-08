---
layout:     post
title:      "javascript一天一练08"
subtitle:   "react-devtools插件"
date:       2019-10-7
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---


##  1.首先打开官网：https://github.com/facebook/react-devtools


## 2.本地打开git bash 然后复制上面的github下载链接
在git中输入：
`git clone https://github.com/facebook/react-devtools.git`
//切换到工程目录
`cd react-devtools`
//切换到v3分支
`git checkout v3`
安装
`npm install`

//安装完成以后切换目录
`cd shells/chrome` //切换到chrome目录下

//然后运行`node build.js` 当前目录下会生成build目录 这个build目录下的unpacked目录就是chrome中所需react-devtools的工具扩展程序包


## 3.到这里有两种方式在chrome浏览器中安装react-devtools
#### 3.1 接着上面在git中将目录切换到react-devtools目录下：
运行命令npm run test:chrome
此时会自动安装react-devtools 并打开chrome浏览器
此时在浏览器右上角的工具栏里打开->更多工具->扩展程序里就可以看到我们安装成功了

#### 3.2:打开chrome浏览器 打开扩展程序
打开开发者模式按钮 选择‘’加载已解压扩展程序‘’选择react-detools目录下的shells->chrome中build目录中的unpacked即可

















