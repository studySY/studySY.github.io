---
title: mysql
date: 2023-04-27 09:57:22
tags:
categories: 学习总结
cover: https://s2.loli.net/2023/05/31/OTd3KZEwMhI42Ue.jpg
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


### mysql数据处理
- 对数据库的直接操作，通过语句直接操作数据库

##### 创建临时表（临时表具有时效性，可能在使用过程中自动销毁掉）

        ```
        -- 创建临时表
        create temporary table '表名'
        -- 删除临时表
        DROP TEMPORARY TABLE '表名';
        --查询临时表
        select * from '临时表名'
        ```
##### 查询到A表中的数据新增到一个不存在的表B中

        ```
        - 创建并将数据新增到B表中
        create table B  select * from A;
        - 将数据插入已经存在的表中（注意查询出的字段名称和将要插入的字段名匹配）
        insert into B select * from A;
        ```
##### 聚合查询
        ```
        /**
        3609406079001311714	多功能	家用组装晒鞋神器落地式铁艺阳台室外晒鞋架子宿舍多功能鞋架挂式	衣帽架卧室宿舍挂衣架家用简约多功能组装挂包置物架简易落地鞋架	3616868857442101304	鞋子收纳架	https://p9-aio.ecombdimg.com/obj/ecom-shop-material/rgNpyAZY_m_6cfef9a620bcd39cd191b6c9974ccf3c_sx_828678_www1080-1080	https://p6-aio.ecombdimg.com/obj/ecom-shop-material/pkpHwDgi_m_e7ce9167982405267b53202aeeafc4b8_sx_95354_www1024-1024

        3609406079001311714	室外	家用组装晒鞋神器落地式铁艺阳台室外晒鞋架子宿舍多功能鞋架挂式	晾晒鞋架室内阳台挂鞋钩窗外防风凉鞋架子室外鞋挂鞋勾晒鞋子神器	3537781505696888549	鞋子收纳架	https://p9-aio.ecombdimg.com/obj/ecom-shop-material/rgNpyAZY_m_6cfef9a620bcd39cd191b6c9974ccf3c_sx_828678_www1080-1080	https://p9-aio.ecombdimg.com/obj/ecom-shop-material/v1_iIvUujMM_70755621364282001950711_0fc69cc5d2dc68e565333b9242871a3b_sx_1033
        */
        
        //将想要聚合的数据进行聚合成为一个串，这样可以将不需要聚合的数据拼在一个传中
        select GROUP_CONCAT(word_res) as word_res,fgoodsname,GROUP_CONCAT(goodsname) as goodsname GROUP BY fgoodsid

        group_concat( [distinct] 要连接的字段 [order by 排序字段 asc/desc ] [separator '分隔符'] )
        SELECT PARENT_ID, GROUP_CONCAT(distinct a.REGION_ID order by a.REGION_ID asc separator ';') GROUP BY PARENT_ID
        *注意事项
        最大值限制GROUP_CONCAT() 是有最大长度限制的，默认值是 1024。当总长度达到 1024 后，后面的记录就被截断掉。可以通过 group_concat_max_len 参数进行动态设置。参数范围可以是 Global 或 Session类型如果group_concat_max_len 的值被设置为小等于 512，那么 GROUP_CONCAT 的返回值类型是 VARCHAR 或 VARBINARY；否则是 TEXT 或 BLOB。实际上，group_concat_max_len 的值可以设置非常大，但会受到参数max_allowed_packet 的限制
        ```