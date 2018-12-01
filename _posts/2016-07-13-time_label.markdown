---
layout: post
title:  "时间label"
date:   2016-07-13 14:28:39  
categories: front
---

```js
//js

function secondsToLabel(rawSeconds) {
    var rawSeconds = rawSeconds || 0;    
    var result = '';

    var minutes = parseInt(rawSeconds / 60);
    var seconds = parseInt(rawSeconds % 60);
    var hours   = parseInt(minutes / 60);
    minutes     = parseInt(minutes % 60);

    if (hours > 0){
        result = hours + "小时"
    }

    if (minutes > 0){
        result = result + minutes + "分"
    }

    if (seconds >= 0){
        result = result + seconds + "秒"
    }

    return result;
}

secondsToLabel(null)
secondsToLabel(undefined)
secondsToLabel('')
secondsToLabel(0)
secondsToLabel(10)
secondsToLabel(100)
secondsToLabel(10000)

```


```ruby
# ruby
result = ""
mm, ss = val.divmod(60)
hh, mm = mm.divmod(60)
result << "#{hh}小时" if hh > 0
result << "#{mm}分"   if mm > 0
result << "#{ss}秒"   if ss >= 0
result
```