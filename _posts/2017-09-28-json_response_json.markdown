---
layout: post
title:  "express response json"
date:   2017-09-28 22:30:39

categories: frontend
---

## express response json

```js
    res.json(data)
```

## mongoose 连接与保存数据
```js
var mongoose = require('mongoose')
// 1. 连接
mongoose.connect('mongodb://test:test@localhost:53494/todos')
// 2. 定义schema
const todoSchema = new mongoose.Schema({
    item: String
})
// 3. 定义model
const Todo = mongoose.model('Todo', todoSchema)
// 4. save model
Todo({ item: 'pick wife up'}).save((err) => {
    if( err) throw err
    console.log('item saved')
})

// find all todos
app.get('/todo', (req, res) => {
    Todo.find({}, (err, data) => {
        if(err) throw err;
        res.render('todo', {todos: data})
    })
})

// save item
app.post('/todo', urlencodedParser, (req, res) => {
    Todo(req.body).save((err) => {
        if(err) throw err;
        res.json(data)
    })
})

// delete item
app.delete('/todo/:item', (req, res) => {
    Todo.find({item: req.params.item}).remove((err, data) => {
        if(err) throw err;
        res.json(data)
    })
})
```