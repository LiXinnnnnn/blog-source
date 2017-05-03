---
title: nginx安装与配置
date: 2017-03-15 13:53:31
tags: nginx
categories : linux
---
# nginx安装与配置

## 说明
  * 安装ngnix需要依赖三个包(附件中已下好)
  * a.gzip模块需要 zlib库 [zlib-1.2.8.tar.gz](http://www.zlib.net/)
  * b.rewrite模块需要 pcre库[pcre-8.38.tar.gz](http://www.pcre.org/) 
  * c.ssl需要openssl库[openssl-1.0.1t.tar.gz](http://www.openssl.org/) 

## 安装openssl
```
  tar zvxf openssl-1.0.1t.tar.gz
  cd openssl-1.0.1t
  ./config --prefix=/app/openssl-1.0.1t    (说明: --prefix:指定安装路径)
  make depend
  make
  make install
  ```
环境变量配置: 
①. vi /etc/profile  （注意权限 切换root账号:sudo su）
②.编辑文件 按I 进入编辑模式
③.在最后一行 添加 export PATH=$PATH:/app/openssl-1.0.1t/bin
④.esc 退出编辑模式
⑤.:wq 保存并推出
⑥.source /etc/profile
⑦.没报错的话 退出重新连接 openssl version可以看出是否成功
## 安装pcre
```
  tar zvxf pcre-8.38.tar.gz
  cd pcre-8.38                    
  ./configure --prefix=/app/pcre-8.38     (说明:prefix:指定安装路径,并且想卸载只要删除这一个文件就行了)
  make
  make install 
```
如果configure报错：
  configure: error: You need a C++ compiler for C++ support.
则，需要用root安装：
  apt-get install build-essential
## 安装zlib
```
   tar zvxf zlib-1.2.8.tar.gz
   cd zlib-1.2.8
   ./configure --prefix=/app/zlib-1.2.8
   make
   make install
```
## 安装nginx
```
    tar zvxf nginx-1.10.0.tar.gz
    cd nginx-1.10.0
    ./configure
    --prefix=/app/nginx-1.10.0
    --with-http_ssl_module              (安装ssl模块,支持https)
    --with-pcre=../pcre-8.38            (注意:指向解压的源码目录)
    --with-zlib=../zlib-1.2.8           (注意:指向解压的源码目录)
    --with-openssl=../openssl-1.0.1t    (注意:指向解压的源码目录)
    (./configure为了方便观看,实际命令是无换行的,但是--前需要空格)
    make
    make install
```
## 启动nginx: 
```
  cd /app/nginx/sbin
  ./nginx 
```
## 重启nginx：
```
  cd /app/nginx/sbin
  ./nginx -s reload    
```
## 关闭nginx: 
```
  kill -9 'cat /app/nginx/nginx.pid'
  或者
  ps -aux|grep nginx
  kill -9 xxx   
```
## nginx配置说明
见[nignx配置文档](http://nginx.org/en/docs/http/ngx_http_proxy_module.html)
