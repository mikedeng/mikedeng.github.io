---
layout: post
title:  "Css3以文本从左到右根据背景渐变"
date:   2018-01-23 22:30:39

categories: frontend
---



## 以文本从左到右根据背景渐变
```scss
    display: inline-block;
    background-image: linear-gradient(to right, $color-primary-light, $color-primary-dark);
    -webkit-background-clip: text;
    color: transparent;
```