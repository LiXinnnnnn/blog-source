---
title: jdk安装
date: 2017-03-15 13:38:41
tags: jdk
categories : linux
---
# jdk安装
```
otauser@OTA:~$ tar zxf jdk-8u73-linux-x64.gz
otauser@OTA:~$ cd /app
otauser@OTA:/app$ cp -r /home/otauser/jdk1.8.0_73/ .

otauser@OTA:/app$ sudo su
root@OTA:/app$ vi /etc/profile

# java env
vi /etc/profile
export JAVA_HOME=/app/jdk1.8.0_73
export JRE_HOME=/app/jdk1.8.0_73/jre
export PATH=$PATH:/app/jdk1.8.0_73/bin
export CLASSPATH=./:/app/jdk1.8.0_73/lib:/app/jdk1.8.0_73/jre/lib
source /etc/profile
```
