---
title: PHP学习
date: 2023-06-01 09:28:11
tags:
categories: 学习总结
cover: https://s2.loli.net/2023/06/01/H9mKU3fxFtX2sSi.jpg
---
### 请求类问题
##### 本地跨域请求设置（添加跨域头）

        ```
        //请求时先进行options请求看是否存在跨域情况，之后再进行头部请求，为防止产生两次请求，我们在这里阻止options请求
        if($_SERVER['REQUEST_METHOD']=='OPTIONS'){
            return 'error';
        }
        header('Access-Control-Allow-Origin: *');
        header('Access-Control-Allow-Headers: *');
        //运行请求的方法
        header("Access-Control-Allow-Methods: *");
        ```
##### TP使用多字段模糊查询
        ```
        $where['tree_path|inviter'] = array(['like', '%' . $account . ',%'], ['like', $account], '_multi' => true);
        
        注： ‘|’：表示 or
        _multi' => true ： 表示多字段
        ————————————————
     
        ```