---
title: apache安装
date: 2017-03-15 13:41:05
tags: apache
categories : linux
---
# linux 环境下apache服务器的安装 
## 1 版本
2.4.18
## 2 安装包准备
  *    pcre-8.37.tar.gz 、
  *    apr-1.5.2.tar、
  *    apr-util-1.5.4.tar.gz
  *    httpd-2.4.18.tar
说明：httpd-2.4.18.tar为apache安装包，另外三个为依赖包。
## 3 步骤
### 3.1  apache 配置，APR依赖缺失，出现error 
otauser@OTA:~/httpd-2.4.18$ ./configure --prefix=/app/apache-2.4.18
configure: error: APR not found.  Please read the documentation.
### 3.2配置apache依赖包 apr-1.5.2 
otauser@OTA:~$ cd apr-1.5.2/
otauser@OTA:~/apr-1.5.2$ ./configure --prefix=/app/apr-1.5.2
otauser@OTA:~/apr-1.5.2$ make
otauser@OTA:~/apr-1.5.2$ make install
### 3.3 apache配置中引入依赖包apr-1.5.2，APR-util依赖缺失，出现error 
otauser@OTA:~/httpd-2.4.18$ ./configure --prefix=/app/apache-2.4.18 --with-apr=/app/apr-1.5.2/
configure: error: APR-util not found.  Please read the documentation.
### 3.4 配置apr-1.5.2 的依赖包apr-util-1.5.4 

otauser@OTA:~/apr-util-1.5.4$ ./configure --prefix=/app/apr-util-1.5.4 -with-apr=/app/apr-1.5.2/bin/apr-1-config
otauser@OTA:~/apr-util-1.5.4$ make
otauser@OTA:~/apr-util-1.5.4$ make install

### 3.5 引入依赖包 apr-util-1.5.4 

otauser@OTA:~/httpd-2.4.18$ ./configure --prefix=/app/apache-2.4.18 --with-apr=/app/apr-1.5.2/ --with-apr-util=/app/apr-util-1.5.4/
configure: error: pcre-config for libpcre not found. PCRE is required and available from http://pcre.org/

### 3.6 如果出现以下error，执行步骤3.7,否则执行步骤3.8

otauser@OTA:~/pcre-8.37$ ./configure --prefix=/app/pcre-8.37
configure: error: You need a C++ compiler for C++ support.

### 3.7 切换到root 用户执行以下命令 

sudo su
root@OTA:/home/otauser# apt-get install build-essential

### 3.8. 配置依赖包 pcre-8.37 

otauser@OTA:~/pcre-8.37$ ./configure --prefix=/app/pcre-8.37 

otauser@OTA:~/pcre-8.37$ make

otauser@OTA:~/pcre-8.37$ make install

### 3.9安装成功 

otauser@OTA:~/httpd-2.4.18$ ./configure --prefix=/app/apache-2.4.18 --with-apr=/app/apr-1.5.2/ --with-apr-util=/app/apr-util-1.5.4/ --with-pcre=/app/pcre-8.37
otauser@OTA:~/httpd-2.4.18$ make
otauser@OTA:~/httpd-2.4.18$ make install

### 3.10启动、关闭apache 的命令 

/app/apache-2.4.18/bin/apachectl start
/app/apache-2.4.18/bin/apachectl stop

