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

### MySQL 事务
- 在 MySQL 中只有使用了 Innodb 数据库引擎的数据库或表才支持事务。
- 事务处理可以用来维护数据库的完整性，保证成批的 SQL 语句要么全部执行，要么全部不执行。
- 事务用来管理 insert,update,delete 语句
- 一般来说，事务是必须满足4个条件（ACID）：：原子性（Atomicity，或称不可分割性）、一致性（Consistency）、隔离性（Isolation，又称独立性）、持久性（Durability）。
    - 原子性：一个事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务开始前的状态，就像这个事务从来没有执行过一样。
    - 一致性：在事务开始之前和事务结束以后，数据库的完整性没有被破坏。这表示写入的资料必须完全符合所有的预设规则，这包含资料的精确度、串联性以及后续数据库可以自发性地完成预定的工作。
    - 隔离性：数据库允许多个并发事务同时对其数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed）、可重复读（repeatable read）和串行化（Serializable）。
    - 持久性：事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。
##### MYSQL 事务处理主要有两种方法：
1、用 BEGIN, ROLLBACK, COMMIT来实现
- BEGIN 开始一个事务
- ROLLBACK 事务回滚
- COMMIT 事务确认（提交）
2、直接用 SET 来改变 MySQL 的自动提交模式:
- SET AUTOCOMMIT=0 禁止自动提交
- SET AUTOCOMMIT=1 开启自动提交
##### thinkPHP5中使用事务案例
```angular2html
//1、引用TP5的think\Db类：use think\Db;
//2、下面为实现代码：
Db::startTrances();//启动事务
try{

update tableName set name = '123' where id = 1;
Db::commit();//提交事务

}catch(\PDOException $e) {

Db::rollback();//回滚

}

```