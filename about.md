---
layout: page
title: "关于我"
permalink: /about
---


2010 年毕业于 [hnrpc](http://hnrpc.com/)，
    做过三年 C#， 两年 Ruby， 现在主要关注前端， 质量才是第一位的。

# 2018-02-16
  码与远方。


# 2016-10-10

  就职于 [Udesk](http://www.udesk.cn)，正在练习英语口语。
  认清自己，不要傲慢。
  对网络请求的一些经验：


   >1. RestClient 一定要设置 timeout, 不然有拖垮server的风险

   >2. 一定要设置 follow_redirection, 并保证response的返回

   >3. 对于失败的worker（sidekiq），要设置 retry .


# 2016-10-12
expriences in git

  * Branches master and develop are not to rebase onto other branches.

  * There are two ways to gather mutiple commits as one.

  >A. Use `git reset start-commit-name`, and commit the changes by force.

  >B. Use `git rebase -i  start-commit-name`, and then apply the fixup option for all of the commits to amend.
