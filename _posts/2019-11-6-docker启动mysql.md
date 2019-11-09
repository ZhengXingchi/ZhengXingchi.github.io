---
layout:     post
title:      "docker启动mysql"
date:       2019-11-6
author:     "ZhengXC"
header-img: "img/post-bg-js-version.jpg"
tags:
    - 前端开发
---

## 用Navicat进行远程连接虚拟机docker启动的mysql无法连接

1. 进入mysql客户端

`docker exec -it c6c8e8e7940f /bin/bash`

其中c6c8e8e7940f是我的mysql的容器名----等价命令 `docker exec -it mysql /bin/bash`

接着`mysql -u root -p123456`

123456就是mysql的登录密码，在docker run的时候设置的

2. ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'newpassword'

3. 如果还不行`firewall-cmd --add-port=3306/tcp`  （放开3306的端口）`firewall-cmd reload `
或者
`sudo systemctl stop firewalld` （关闭防火墙）
 












 










