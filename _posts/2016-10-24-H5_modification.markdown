---
layout: post
title:  "H5 modication"
date:   2016-10-25 20:30:39

categories: frontend
---

 H5 modication：



## 新增结构标签

* header  页眉
* nav         页面导航的链接组
* section   页面中的一个内容区块，通常由内容及标题组成
* aside      非正文内容
* footer    脚注

## 新增网页元素

* video    视屏
* audio    音频
* canvas  图形
* datalist  可选数据列表，常用子标签`option`,  input 标签通过 `list` 属性与它关联

* time       日期与时间
* mark      突出的文字
* progress 运行中的进度, 常用属性 `value`， `max`

## 新增全局属性

* contentEditable 内容可编辑
* designMode 整个网页可编辑
* hidden       隐藏元素
* spellcheck 编写检查
* tabindex     tab index

## 废除元素

* 能用 css替代的元素 `big`, `center`, `font`, `s`,  `u`,  `strike`
* 不再使用`frame` 框架
* 只有部分浏览器支持的元素 `applet` `blink` `bgsound` `marquee`

## 废除属性(可以用css代替)

* table (`align` `bgcolor` `border` `cellpadding` `width`)
* html (`version`)
* a/link (`charset`)
* br (`clear` )
* img (`align`)

## css3的高级选择器

* first-of-type
* last-of-type
* last-child
* nth-child(n)  n = number or num = `even` or num = `odd`
* :before
* :after

## 新的 input 类型

 * email
 * url
 * number
 * range  滑动条
 * search
 * date pickers   日期

## input 类型 - Date pickers

 * date
 * month
 * week
 * time
 * datetime
 * datetime-local

## 新增 input 属性

  * autofocus
  * required
  * placeholder
  * pattern
  * height, width 只适用 image 类型的 input 标签

## validityState 对象

  * valueMissing
  * typeMismatch
  * patternMismatch
  * tooLong

## input 用于验证的伪类

  * valid
  * invalid
