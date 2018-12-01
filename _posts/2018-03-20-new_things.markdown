---
layout: post
title:  "今日摘要"
date:   2018-03-20 20:33:39

categories: frontend
---

## lodash api

+ times: 执行多次函数
```js
    _.times(10, function(){
        person.age = _.random(40);
    });
```

>  more
```js
    // 生成字符数组
    _.times(3, String); // [“0”， “1”， “2”]
```


## mobx api
+ autorun

```js
    var person = mobx.observable({
        firstName: 'Matt',
        lastName : 'Ruby',
        age      : 34,
        fullName: function(){
            return this.firstName + ' ' + this.lastName;
        }
    });

    mobx.autorun(function(){
        console.log(person.firstName + ' ' + person.age);
    })

    person.firstName = 'Mike'
```