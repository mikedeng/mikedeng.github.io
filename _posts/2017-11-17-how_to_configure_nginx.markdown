---
layout: post
title:  "nginx配置入门"
date:   2017-11-16 22:30:39

categories: frontend
---



## 处理请求的方式
   +  Apache: 线程或进程
   +  Nginx:  异步事件驱动模型

## 动态资源的处理方式
  + Apache: 内置，可以自己处理

  + Nginx:  没内置，交给其它的 `CGI`, `FastCGI`或者 `Apache` 处理，完成之后再转发到 `client`



## 修改前注意事项
+ 一定要对配置文件夹做好备份，可以用 Git， 也可以用 copy
```zsh
    cp /etc/nginx/nginx.conf /etc/nginx/nginx.conf.$(date "+%b_%d_%Y_%H.%M.%S")
```


配置文件语法
+ 每一个配置项都是一个 `key value pair`，然后用逗号 `;` 结束
+ 指令 value 可以一个单值，也可以是一个对象，这个对象其中包括其它指令

指令的定义

> 示例代码
```nginx
    user www-data;
    worker_processes 4;
    pid /run/nginx.pid;

    events {
            worker_connections 768;
            # multi_accept on;
    }
```

## http
+ `user` 指定某个用户拥有和运行 `nginx`
+ `worker_processes` 指定运行的线程或并发实例
+ `pid` 主进程id，或PID。操作系统可以通过这个id对实例进行追踪或发送信号。


## server
+ `server_name` nginx 可以设置任意域名， nginx只是使用这个名称来回应请求。
+ `location` 在明确定义时，它总是从最多级匹配，没有先后之分, 比如 `location /planet/blog/`

```nginx
    location / { }
    location /images/ { }
    location /blog/ { }
    location /planet/ { }
    location /planet/blog/ { }
```

+ `~` 后面跟正则，它是区分大小写的.
下面的匹配 `IndexPage.php`，但不匹配 `indexpage.php`
```nginx
    location ~ IndexPage\.php$ { }
```
+ `~*` 后面跟正则， 它不区分大小写
```nginx
    location ~* \.(pl|cgi|perl|prl)$ { }
```

+ `^~ ` 有先后顺序的匹配


引用
+ [configure](https://www.linode.com/docs/web-servers/nginx/how-to-configure-nginx/)

+ [worker_processes](http://nginx.org/en/docs/ngx_core_module.html#worker_processes)