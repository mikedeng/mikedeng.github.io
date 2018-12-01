---
layout: post
title:  "深复制js对象"
date:   2017-08-16 22:30:39

categories: frontend
---


+ 问题： js如何实现`浅`复制

+ 解决办法：

	```javascript

		function Person(name){
			this.name = name;
		};

		var common = new Person('xxx');
		common.hobbies = ['run'];


		function extendCopy(p, c){
			var i, c = c || {};
			for(i in p){
				c[i] = p[i];
			}
			return c;
		};

		var mike = extendCopy(common);
		mike.name = 'mike';

		mike.hobbies.push('swim');

		console.log(common.hobbies);
		console.log(mike.hobbies);

	```

	+ 问题： js如何实现`深`复制

	+ 解决办法：

	```javascript

		function deepCopy(p, c) {
			var i, c = c || {};

			for(i in p){
				if( typeof p[i] === 'object' ) {
					c[i] = (p[i].constructor === Array) ? [] : {}
					deepCopy(p[i], c[i]);
				}else{
					c [i] = p [i];
				}
			}

			return c;
		};

		var mike = deepCopy(common);
		mike.name = 'mike';

		mike.hobbies.push('swim');

		console.log(common.hobbies); // ['run']
		console.log(mike.hobbies);   // ['run', 'swim']

	```