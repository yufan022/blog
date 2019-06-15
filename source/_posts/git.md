---
title: Git常用命令
date: 2019-06-15 17:20:51
tags: git
categories: command
---
## 记录常用git命令
<!-- more -->
- git pull所有远程分支
    ```
    git branch -r | grep -v '\->' | while read remote; do git branch --track "${remote#origin/}" "$remote"; done
    git fetch --all
    git pull --all
    ```
- 秘钥
    ```
    // 设置全局
    git config --global user.name “用户名”
    git config --global user.email “邮箱”
    // 生成秘钥
    ssh-keygen -t rsa
    // 查看秘钥
    cat ~/.ssh/id_rsa.pub
    // 生成多个秘钥
    ssh-keygen -t rsa -C 'second@mail.com' -f id_rsa_second
    // ~/.SSH config文件配置秘钥映射
    Host gitlab.xxx.com ##可以随意命名，链接时使用这个名字  
        HostName gitlab.xxx.com  
        User git  
        Port 22  
        IdentityFile ~/.ssh/id_rsa_second
    // 测试配置文件是否正常
    ssh -T git@gitcafe.com
    ```
