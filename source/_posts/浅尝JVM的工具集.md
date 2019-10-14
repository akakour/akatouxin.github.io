---
title: 浅尝JVM的工具集
tags:
  - java
  - jvm
categories:
  - jvm性能优化
date: 2019-10-13 00:02:36
---

## jps

出当前机器上正在运行的虚拟机进程

**常用参数**：

-p  :仅仅显示VM 标示，不显示jar,class, main参数等信息。

-m:输出主函数传入的参数. 下的hello 就是在执行程序时从命令行输入的参数。

-l: 输出应用程序主类完整package名称或jar完整名称。

-v: 列出jvm参数。

![1570972092188](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjps-v.png)

## jstat

是用于监视虚拟机各种运行状态信息的命令行工具。它可以显示本地或者远程虚拟机进程中的类装载、内存、垃圾收集、JIT编译等运行数据，在没有GUI图形界面，只提供了纯文本控制台环境的服务器上，它将是运行期定位虚拟机性能问题的首选工具。

**常用参数**：

-class (类加载器) 

![1570971860655](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjstat-class.png)

-compiler (JIT) 

![1570971906439](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjstat-compiler.png)

-gc (GC堆状态) 

![1570971593197](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjstat-gc.png)

-gccapacity (各区大小) 

-gccause (最近一次GC统计和原因) 

![1570971685800](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjstat-gccause.png)

-gcnew (新区统计)

-gcnewcapacity (新区大小)

-gcold (老区统计)

-gcoldcapacity (老区大小)

-gcpermcapacity (永久区大小)

-gcutil (GC统计汇总)

![1570972016673](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjstat-gcutil.png)

-printcompilation (HotSpot编译统计)

![1570971790271](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjstat-printcomplition.png)

## jinfo 

查看和修改虚拟机的参数

jinfo –sysprops 可以查看由System.getProperties()取得的参数

![1570972241200](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjinfo-sysprops.png)

jinfo –flag 未被显式指定的参数的系统默认值

jinfo –flags（注意s）显示虚拟机的参数

![1570973306003](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_posts%5C%E6%B5%85%E5%B0%9DJVM%E7%9A%84%E5%B7%A5%E5%85%B7%E9%9B%86%5Cjinfo-flags.png)

jinfo –flag +[参数可以增加参数，但是仅限于由查询出来且