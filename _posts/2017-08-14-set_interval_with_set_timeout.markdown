---
layout: post
title:  "用 setTimeout实现setInterval"
date:   2017-08-14 22:30:39

categories: frontend
---


+ 问题： 这个问题是一面试官问的 -- 如何用 setTimeout 实现 setInterval 并 clearTimeout

+ 解决办法：

	```javascript

	function Interval(fn, ms){
		return {
			timer_id: null,
			start: function(){
				var that = this;
				if(this.timer_id) { that.clear(); }
				this.timer_id = setTimeout(
					function(){
						fn();
						that.start();
					}, ms)
			},
			clear: function(){
				clearTimeout(this.timer_id);
			}
		}
	}

	var sum = 0;
	obj = Interval(function(){ console.log(sum++)}, 1000);
	obj.start();  // start interval

	obj.clear(); // clearTimeout

	```