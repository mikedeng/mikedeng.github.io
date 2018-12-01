---
layout: post
title:  "atom 菜单支持中文字体"
date:   2016-04-15 17:08:39
categories: linux
---

##### edit -> open your stylesheet

```less
@font-size: 14px;
@font-family: 'DejaVu Sans Mono', '文泉驿正黑';
html, body, .tree-view, .tab-bar .tab {
  font-size: @font-size;
  font-family: @font-family;
}
```
