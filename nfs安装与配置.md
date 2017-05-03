---
title: nfs安装与配置
date: 2017-03-15 13:47:00
tags: nfs
categories : linux
---
### nfs服务器安装软件：  
  sudo apt-get install nfs-kernel-server 
  (安装nfs-kernel-server时，apt会自动安装nfs-common和rpcbind)
  
### nfs客户端安装软件：
  sudo apt-get install nfs-common
  (安装nfs-common时，apt会自动安装rpcbind)
  
### nfs服务端配置：
  sudo vi /etc/exports
  添加行：
  /app/nfs/ota-package 172.16.91.25(rw,sync,no_root_squash,no_subtree_check)
### nfs服务端启动：
  sudo service portmap restart
### nfs客户端执行：
  sudo mount 172.16.22.22:/app/nfs/ota-packages /app/webContent/ota-packages
  
客户端重启后，需要重新运行上面的mount命令；重新运行，则客户端文件夹内容将被主服务器文件夹内容覆盖；所以建议源文件夹作为服务端。
nfs源文件在服务器端，如果设计大量读取请求，则必须让请求直接访问nfs服务器端，而不是访问nfs客户端。所以建议下载服务器端作为服务器端。

### 查询本机所有mount信息：
  mount