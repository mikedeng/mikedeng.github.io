---
layout: post
title:  "custom events implementation in js"
date:   2016-10-19 20:40:39  

categories: frontend
---

 实现用户自定义事件：

```js
//Copyright (c) 2010 Nicholas C. Zakas. All rights reserved.
//MIT License

function EventTarget(){
	this._listeners = {};
}

EventTarget.prototype = {
	constructor: EventTarget,

	addListener: function(type, listener){
		if(typeof this._listeners[type] == "undefined"){
			this._listeners[type] = [];
		}

		this._listeners[type].push(listener);
	},

	fire: function(event){
		var listeners, i, len;

		if(typeof event == "string"){ event = {type: event}; }
		if(!event.target){ event.target = this; }
		if(!event.type){ throw new Error("Event object missing 'type' property."); }

		if(this._listeners[event.type] instanceof Array){
			listeners = this._listeners[event.type];
			for(i = 0, len = listeners.length; i < len; i++){
				listeners[i].call(this, event);
			}
		}
	},

	removeListener: function(type, listener){		
		var listeners, i, len;

		if(this._listeners[type] instanceof Array){
			listeners = this._listeners[type];
			for(i, len = listeners.length; i < len; i++){
				if( listeners[i] === listener ){
					listeners.splice(i, 1);
					break;
				}
			}
		}
	}
}


// use example
var target = new EventTarget();
function handleEvent(event){
    alert(event.type);
};

target.addListener("foo", handleEvent);
target.fire({ type: "foo" });    //can also do target.fire("foo")
target.removeListener("foo", handleEvent);


// use example with inheriting
function MyObject(){
    EventTarget.call(this);
}

MyObject.prototype = new EventTarget();
MyObject.prototype.constructor = MyObject;
MyObject.prototype.foo = function(){
    this.fire("foo");
};

var o = new MyObject();

o.addListener("foo", function(){
    alert("Foo just happened.");
});

o.foo();

```


original from [nick's blog](https://www.nczonline.net/blog/2010/03/09/custom-events-in-javascript/)
