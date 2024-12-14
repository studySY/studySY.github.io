---
title: Css学习
date: 2024-12-14 13:36:00
tags:
categories: 学习总结
cover: https://s2.loli.net/2024/12/14/pN64PgcvDCXAqax.png
---
### Css干货

##### Css标签背景相关
    //背景颜色
    - background-color：#fff   
    //背景图片（默认图片重复）
    - background-image：url("图片地址")
    //设置图片是否重复（如果不加入repeat，默认为重复）
    - background-repeat：no-repeat(不允许重复)、repeat-x(水平重复)、repeat-y(垂直重复)、repeat(水平垂直都重复)
    - background-position：center center(默认)、left top(左上角)、right bottom(右下角)、50% 50%(50% 50%为图片中心)
    //right 右边从图片中间开始显示
    - background-position：right
    - background-attachment：fixed(背景固定，不随滚动条滚动)、scroll(背景随滚动条滚动)

    - background-size：cover(图片填满整个背景)、contain(图片自适应背景)
    - background-origin：border-box(默认，背景从边框开始)、padding-box(背景从内边距开始)、content-box(背景从内容开始)
    - background-clip：border-box(默认，背景从边框开始)、padding-box(背景从内边距开始)、content-box(背景从内容开始)

##### Css文本相关
    //文本颜色
    - color：#fff
    //文本方向
    - direction：rtl(从右向左)
    //行高
    - line-height：1.5em(行高)
    //字符间距
    - letter-spacing：1px(字间距)
    //对齐元素中的文本
    - text-align：left(默认)、right、center、justify
    //向文本添加修饰
    - text-decoration: none(默认)、underline(下划线)、overline(上划线)、line-through(删除线)
    //缩进元素中文本的首行
    - text-indent：2em(缩进2em)
    //文本溢出省略号
    - text-overflow：ellipsis(省略号)
    //文本换行
    - white-space：nowrap(默认，不换行)、pre(保留空格换行)、pre-wrap(保留空格换行，但超过一行换行)、pre-line(保留空格不换行，但超过一行换行)
    //元素中的字母
    - text-transform：capitalize(首字母大写)、uppercase(全部大写)、lowercase(全部小写)
    //设置文本方向
    - unicode-bidi：normal(默认)、embed(嵌入)、bidi-override(重写)
    //字间距
    - word-spacing：1px(字间距)
    //向文本添加阴影
    - text-shadow：1px 1px 1px #000(阴影)
    //规定文本的换行规则
    - word-wrap：normal(默认)、break-word(强制换行)