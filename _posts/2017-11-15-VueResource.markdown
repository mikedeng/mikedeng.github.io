---
layout: post
title:  "VueResource的一些设置"
date:   2017-11-15 22:30:39

categories: frontend
---


+ 设置头部
    ```js
    // main.js
    Vue.http.options.root = 'https://ng-http-1528d.firebaseio.com/data.json'
    ```
+ 设置headers
    ```js
    // main.js
    Vue.http.headers.common['Authorization'] = 'Basic YXBpOnBhc3N3b3Jk';
    ```

+ interceptors
    ```js
    // main.js
    Vue.http.interceptors.push(function(request, next){
        request.headers['Authorization'] = 'YXBpOnBhc3N3b3Jk'

        next(response => response.json )
    })
    ```

+ custom actions & URI template
    ```js
    data(){
        return {
            ...
            resource: {},
            node: 'data'
        }
    }
    , methods: {
        submit(){
            this.resource.saveAlt(this.user)
        },fetchData(){
            this.resource.getData({node: this.node})
        }
    },
    created(){
        const customActions = {
            saveAlt: { method: 'POST', url: 'alternative.json' },
            getData: {method: 'GET'}
        }

        this.resource = this.$resource('{node}.json', {}, customActions)
    }
    ```


### 引用

1. [Vue Resource 文档](https://github.com/pagekit/vue-resource/tree/develop/docs)

2. [URI template](http://medialize.github.io/URI.js/)