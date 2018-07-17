---
title: nginx+tomcat集群
copyright: true
date: 2018-06-10 10:39:16
tags: 集群
categories: 分布式
---

# 安装nginx软件装备

* 安装GCC：yum install -y gcc-c++
* 安装PCRE pcre-devel:    yum install -y pcre pcre-devel
* 安装zlib:    yum install -y zlib zlib-devel
* 安装OpenSSL:    yum install -y openssl openssl-devel

<!-- more -->

# Nginxa安装

* http://nginx.org/en/download.html
* tar -zxvf nginx-1.14.tar.gz
* ./configure  默认生成在/usr/local/nginx下
* make & make install
* ./sbin/nginx启动  ./sbin/nginx -s reload重新加载配置文件

# tomcat集群配置

```
 upstream edu.com {
        server  192.168.239.131:8080  weight=1;
        server  192.168.239.132:8080  weight=1;
        server  192.168.239.133:8080  weight=1;

    }
server{
    location / {
            proxy_pass http://edu.com;
            proxy_redirect default;
        }
}
```





