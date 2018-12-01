---
layout: post
title:  "安装nginx并配置静态资源路径出现403"
date:   2017-11-16 22:30:39

categories: frontend
---


+ 手动源码安装 `nginx` 时会需要 `gcc+`, `zlib`, `prce` 等库

## 安装nginx
```zsh
# 1. 方法一
yum install nginx

# 2. 方法二
./configure —-prefix=/usr/local/nginx —-with-prce=/prce/path —-with-zlib=/zlib/path

make && make install
```

## 解决 403
+ 新建用户并添加 sudo 权限  [*选做*]
```zsh
useradd liutian
passwd liutian

# 添加 liutian 为 sudo 权限
sudo vi /etc/sudoers
liutian  ALL = (ALL) ALL
```

```zsh
# 检查目录是否有执行权限 x
namei -om /home/liutian/ec-cloud/

# 设置没有执行权限 x 的目录
chmod o+x /home
```
## 配置静态资源路径

```zsh
server {
    listen 8088;
    server_name localhost;
    ...

    # 设置静态资源
    location /static/ {
        alias /var/www/ec-cloud/static;
    }
```

### 参考
1. [execution check](https://stackoverflow.com/questions/6795350/nginx-403-forbidden-for-all-files)
2. [static alias](https://gist.github.com/vishaltelangre/bcc95485b97f534a8c27)