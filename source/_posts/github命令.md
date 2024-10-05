---
title: github命令
date: 2023-06-01 09:39:02
tags:
categories: 学习总结
cover: https://s2.loli.net/2023/06/01/gnxaLjuDhvIOkeS.jpg
---
### github干货

##### github初次提交代码

    ```
    # 初始化本地仓库（如果你之前没有这么做）
    git init
    # 添加远程仓库地址（将URL替换为你的远程仓库地址）
    git remote add origin <远程仓库URL>
    # 添加文件到暂存区
    git add .
    # 提交更改
    git commit -m "提交备注"
    # 将本地的 master 分支推送到远程仓库，同时设置上游（upstream）
    git push -u origin master
    
    ```



##### github提交代码（提交过程中断网、遗忘）

    ```
        //原本已经commit的代码由于某些原因（遗忘、断网...）没有提交到远程服务器，导致你没有完成工作
        git cherry 
        git init
        git remote add origin https://e.coding.net/lv136194452/gerenziliao/myblod.git
        git add -A
        git commit
        git push -u origin master
        ```
##### github拉取远程代码到本地

    ```
        git init
        
        
        git clone <远程仓库URL>
        
    ```