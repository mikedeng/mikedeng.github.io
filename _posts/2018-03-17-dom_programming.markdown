---
layout: post
title:  "摘要 -- DOM 编程艺术"
date:   2018-03-17 19:33:39

categories: frontend
---

## 定义

### 宿主对象 （host object)
除了内建对象，还可以在js脚本里使用一些已经预先定义好的其他对象。这些对象不是由js语言本身而是由它的运行环境提供的。具体到 Web 应用，这个环境就是浏览器。由浏览器提供的预定义对象被称为宿主对象（host object)。
宿主对象包括 Form、Image和Element等。我们可以通过这些对象获得关于网页上表单、图像和各种表单元素等信息。


## Tips
+ 函数在行为方面应该像一个自给自足的脚本，在定义一个函数时， 我们一定要把它内部的变量全都明确地声明为局部变量。

+ DOM并不是与网页结构打交道的唯一技术。还可以通过CSS告诉浏览器如何显示一份文档的内容。

+ element.setAttribute 实际完成了两项操作
    > 创建这个属性

    > 设置这个属性的值


## 代码

用 `getElementsByTagName` 实现 `getElementsByClassName`
```js
    function getElementsByClassName(node, classname){
      if(node.getElementsByClassName){
        return node.getElementsByClassName(classname)
      }else {
         var results = new Array();
         var elems = node.getElementsByTagName('*');
        for(var i = 0; i < elems.length; i++) {
          if(elems[i].className.indexOf(classname) !== -1){
              results[results.length] = elems[i];
          }
        }

        return results;
      }
    }
```


## 要解决的问题
+ 当在最外层定义 var a = 1; 时，a === window.a。 当定义函数 function f1() {} 时， f1 === window.f1。
+ 当在函数里面定义时呢？
    ```js
        function f(){
            var a = 1;

            function b(){

            }
        }
    ```