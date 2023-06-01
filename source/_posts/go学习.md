---
title: go学习
date: 2023-06-01 09:23:23
tags:
categories: 学习总结
cover: https://s2.loli.net/2023/06/01/WUIQtV3eAGwzFXj.jpg
---
### 下载地址
- Go官网下载地址：https://golang.org/dl/ (打开有点慢)
  - 一定要记住安装位置
### 配置GOPATH
- GOPATH是一个环境变量，用来表明你写的go项目的存放路径
- GOPATH路径最好只设置一个，所有的项目代码都放到GOPATH的src目录下。
##### windows设置环境变量
- 我的电脑->属性->高级系统设置
  - 检查一下你的电脑里面是否存在`GOPATH`并且设置值为你要存`go`代码的目录
  - 如果没有新建一个`GOPATH`，同时将值设置为你`go`项目的根目录
  - 同时在`path`里面添加`go`的安装目录和`GOPATH`目录(自我感觉有异议，直接配置环境变量`path`可能就会好用，我的本地是直接配置的`path`变量)
### 第一个go程序
- 在`go`程序中新建三个文件夹分别是：`bin`(用来存放编译后生成的可执行文件)、`pkg`(用来存放编译后生成的归档文件)、`src`(用来存放源码文件)
  - 在`src`目录下创建一个`hello目录`，在`hello目录`中创建一个`main.go`文件：
  ```
    package main          //声明main包，表名当前是一个可执行程序

    import "fmt"          //导入内置 fmt

    func main(){  // main函数，是程序执行的入口
        fmt.Println("Hello World!")  // 在终端打印 Hello World!
    }
  ```