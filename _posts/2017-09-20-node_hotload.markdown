---
layout: post
title:  "Node热更新hotload"
date:   2017-09-20 22:30:39

categories: frontend
---

## 创建事件的方法

```js
var EventEmitter = require('events')
class MyEmitter extends EventEmitter { }
var myEvt = new MyEmitter()
myEvt.on('myEvent', (msg) =>{
  console.log(msg)
})

myEvt.emit('myEvent', 'event is emitted')
```

## 事件与 util
```js
var EventEmitter = require('events')
var util = require('util')

var Person = function(name) {
  this.name = name
}

util.inherits(Person, EventEmitter)

var james = new Person('james')
var mary = new Person('mary')
var ryu = new Person('ryu')

var people = [james, mary, ryu]
people.forEach((person) => {
  person.on('speak', (msg) => {
    console.log(person.name + ' said ' + msg)
  })
})

james.emit('speak', 'hey dudes')
ryu.emit('speak', 'I wanna a curry')
mary.emit('speak', 'Come home now')
```
## file 读写
```js
var fs = require('fs')
fs.readFile('readme.txt', 'utf8', (err, data) => {
  fs.writeFile('readme3.txt', data, (err2) => {
    console.log('write done!!')
  })
})

console.log('here first')
```

## file 更多操作
```js
  const fs = require('fs')
  // 异步删除文件
  fs.unlink('filename.txt',()=> {})

  // 同步创建目录
  fs.mkdirSync('stuff')

  // 同步删除目录
  fs.rmdirSync('stuff')

  // 异步创建目录
  fs.mkdir('stuff')

  // 异步删除目录
  fs.rmdir('stuff')

  // 删除目录下所有文件，fs.readdir & fs.unlink & path.join
  fs.readdir(dir, (err, files) => {
    if(err) throw err
    for(const file of files) {
      fs.unlink(path.join(dir, file), err2 => {
        if(err2) throw err2
      })
    }
    fs.rmdir(dir)
  })

```

## http server
```js
var http = require('http')
var server = http.createServer((req, res) => {
  console.log('request was made: ' + req.url)
  res.writeHead(200, {'Content-Type': 'text/plain'})
  res.end('hey node ninjas')
})

server.listen(3000)
console.log('listening on port 3000')
```

## read write stream
```js
var http = require('http')
var fs = require('fs')

var myReadStream = fs.createReadStream(__dirname + '/readme.txt', 'utf8')
var myWriteStream = fs.createWriteStream(__dirname + '/readmew.txt')
myReadStream.on('data', function(chunk){
  console.log('new chunk received: ')
  console.log(chunk)
  myWriteStream.write(chunk)
})

// 或者直接使用 pipe， 它里面包含了 on('data') 事件, 它可以用在 response上
myReadStream.pipe(myWriteStream)
```

## express with template
```js
var express = require('express')
var app = express()
var bodyParser = require('body-parser')
// body parser
var urlencodedParser = bodyParser.urlencoded({ extended: false})
// 配置视图引擎
app.set('view engine', 'ejs')
// serve 静态文件
app.use('/assets', express.static('css'))
app.get('/', (req, res) => {
  res.send('this is the home page')
})

app.get('/profile/:name', (req, res) => {
  console.log(req.params.name)
  res.render('profile')
})

app.post('/contact', urlencodedParser, (req, res) => {
  // 获取 body parser 里面的值
  console.log(req.body.name)
})
```
