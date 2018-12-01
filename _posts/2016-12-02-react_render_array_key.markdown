---
layout: post
title:  "react render key error"
date:   2016-12-02 22:30:39

categories: frontend
---


问题： 从 array　绑定了一个列表，　添加两条数据，删除第一条 item 时，更新view时，第一条还在，而把第二条给删掉了

+   猜测是从 array　中删除错了，尝试调试　array　的保留项，发现没有错

+   猜测是 render　更新延迟, 尝试添加forceUpdate, 发现没用
 
+   检查 render 中 item 的绑定, 发现 key 是用的 map 函数的 index，发现问题

    原因:
      当删掉第一条数据时，　array还剩下一条数据， key = index = 0, 所以，原来的第一条依然保留。

    解决办法：

    设置 key = id
