---
title: github命令
date: 2023-06-01 09:39:02
tags:
categories: 学习总结
cover: https://s2.loli.net/2023/06/01/gnxaLjuDhvIOkeS.jpg
---
### github干货
##### github提交代码

    ```
        //原本已经commit的代码由于某些原因（遗忘、断网...）没有提交到远程服务器，导致你没有完成工作
        git cherry 
        git init
        git remote add origin https://e.coding.net/lv136194452/gerenziliao/myblod.git
        git add -A
        git commit
        git push -u origin master
        ```