---
title: 虚拟机中固定IP配置
tags:
  - Linux
  - 后端
categories:
  - Linux
date: 2019-08-24 23:05:09
---
![1569333826573](虚拟机中固定IP配置/1569333826573.png)

# 虚拟机CentOS固定IP怎么配置？

1. VMWare中选择桥接模式

2. 查看主机的ip段，cmd中输入**ipconfig**，并记下。例：本机ip：192.168.11.4

3. vi /etc/sysconfig/network-scripts/ifcfg-eth0  (每台机器网卡可能不一样，所以这个文件可能不太但是文件名都是**ifcfg-XXX**)，并修改以下内容并保存：

   ```xml
   TYPE=Ethernet
   ONBOOT=yes
   BOOTPROTO=static //静态ip
   IPADDR=192.168.11.5 //上一步中查看的宿主机ip段，但不能是相同ip，修改最后域
   GATEWAY=192.168.11.1 
   NWTMASK=255.255.255.0 //一般是这个固定值
   DNS1=8.8.8.8
   ```

4. 重启网络服务：service network restart
