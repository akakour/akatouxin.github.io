---
title: 浅尝JVM执行子系统
tags:
---

![1571062268857](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_drafts%5C%E6%B5%85%E5%B0%9DJVM%E6%89%A7%E8%A1%8C%E5%AD%90%E7%B3%BB%E7%BB%9F%5Chead.png)

# JVM执行子系统——类加载器

## Class类文件

### Class类的本质

Class文件时一个以8字节为基础单位的二进制流。

类似于C里面结构体的伪结构体来储存数据。

只有两种数据类型：无符号数和表。

无符号数属于基本的数据类型，以u1、u2、u4、u8

表是由多个无符号数或者其他表作为数据项构成的复合数据类

### Class文件格式

```C++
ClassFile { 
    u4 magic;  // 魔法数字，表明当前文件是.class文件，固定0xCAFEBABE
    u2 minor_version; // 分别为Class文件的副版本和主版本
    u2 major_version; 
    u2 constant_pool_count; // 常量池计数
    cp_info constant_pool[constant_pool_count-1];  // 常量池内容
    u2 access_flags; // 类访问标识
    u2 this_class; // 当前类
    u2 super_class; // 父类
    u2 interfaces_count; // 实现的接口数
    u2 interfaces[interfaces_count]; // 实现接口信息
    u2 fields_count; // 字段数量
    field_info fields[fields_count]; // 包含的字段信息 
    u2 methods_count; // 方法数量
    method_info methods[methods_count]; // 包含的方法信息
    u2 attributes_count;  // 属性数量
    attribute_info attributes[attributes_count]; // 各种属性
}
```

> 1. **魔数与Class文件的版本**
> 2. **常量池**
> 3. 访问标志
> 4. 类索引、父类索引与接口索引集合
> 5. 字段表集合
> 6. 方法表集合
> 7. 属性表集合

![1571065172076](C:%5CUsers%5CLuoXin%5CWebstormProjects%5Cakatouxin.github.io%5Csource%5C_drafts%5C%E6%B5%85%E5%B0%9DJVM%E6%89%A7%E8%A1%8C%E5%AD%90%E7%B3%BB%E7%BB%9F%5Cclass-formate.png)