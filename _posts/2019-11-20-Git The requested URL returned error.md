---
layout:     post
title:      "Git The requested URL returned error: 403"
date:       2019-11-20
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---


##  参考资料
[git 缓存密码导致的不能和远程仓库交互unable to access... 403错误](https://www.jianshu.com/p/77b0340a02f3)
[Git The requested URL returned error: 403](https://www.jianshu.com/p/a1908f55bef8)

## 指令

执行`git config --list`，查看git的配置信息

执行vim /User/[你的用户名]/.git-credentials，查看credential中缓存的账户


如果输入了 git config credential.helper 命令之后还是出现了osxkeychain， store 或者 cache 等，说明 git 的配置还是没有被清空，我参考了stackOverFlow上这个问题 有人给了这样一个命令查看 credential.helper 所在的文件目录(可能一个电脑上有多个.gitconfig文件)，

```
git config --show-origin --get credential.helper
file:/Applications/Xcode.app/Contents/Developer/usr/share/git-core/gitconfig    osxkeychain
```


重新配置
git  config --global  credential.helper  store 



 
 












 










