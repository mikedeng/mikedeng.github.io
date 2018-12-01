---
layout: post
title:  "Graceful degradation @supports"
date:   2018-02-19 17:01:39

categories: frontend
---

```scss
    @supports(clip-path: polygon(0 0)) or (-webkit-clip-path: polygon(0 0)) {
        -webkit-clip-path: polygon(0 0, 100% 0, 100% 75vh, 0 100%);
        clip-path        : polygon(0 0, 100% 0, 100% 75vh, 0 100%);
        height           : 95vh;
    }
```