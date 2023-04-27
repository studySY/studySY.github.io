---
title: mysql
date: 2023-04-27 09:57:22
tags:
---
## mysql关系型数据库(Relational Database Management System)
### MySQL 创建数据库
- 我们可以在登陆 MySQL 服务后，使用 create 命令创建数据库，语法如下:
```
create database 数据库名称
```
- 以下命令简单的演示了创建数据库的过程，数据名为 local:
```
//连接数据库
[root@host]# mysql -u root -p   
Enter password:******  # 登录后进入终端
//创建数据库
mysql> create database local;
```
##### 使用 mysqladmin 创建数据库
- 使用普通用户，你可能需要特定的权限来创建或者删除 MySQL 数据库。所以我们这边使用root用户登录，root用户拥有最高权限，可以使用 mysql mysqladmin 命令来创建数据库。以下命令简单的演示了创建数据库的过程，数据名为 RUNOOB:
```angular2html
//执行成功后会创建 MySQL 数据库 RUNOOB。
[root@host]# mysqladmin -u root -p create local
Enter password:******

```