---
layout:     post
title:      "vscode调试以及调试webpack"
date:       2019-11-7
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---


## 调试webpack
`npx node --inspect-brk ./node_modules/.bin/webpack --inline --progress --config 配置地址`
打开chrome 输入chrome://inspect
在webpack.config.js打debugger


## vscode
小虫子图标点击=>add configuration=>选择nodejs环境=>修改配置
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "nodemon",
            "runtimeExecutable": "${workspaceFolder}/node_modules/.bin/nodemon",
            "program": "${workspaceFolder}/src/index.js",
            "restart": true,
            "console": "integratedTerminal",
            "internalConsoleOptions": "neverOpen",
            "runtimeArgs":["--exec","babel-node"]
        }
    ]
}
```


 
 












 










