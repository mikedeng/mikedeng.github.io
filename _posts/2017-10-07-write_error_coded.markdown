---
layout: post
title:  "Node file writer乱码问题"
date:   2017-10-07 22:30:39

categories: frontend
---

```js
const fs = require('fs')
// 中文
str = '床前明月光，疑似地上霜，举头望明月，低头思故乡'
fs.writeFileSync('test.md', str)

// 这样会造成乱码
var rs = fs.createReadStream('test.md', {highWaterMark: 11})
// 消除乱码
rs.setEncoding('utf8')
var data = ''
rs.on('data', function (chunk) {
  data += chunk
})

rs.on('end', () => {
  console.log(data)
})
```