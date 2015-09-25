---
layout: post
title: linux下批量替换文件内容
categories: linux基础
tags: linux常用命令
date: 2015-09-14 16:35:30
---
---
## demo

```bash
    sed -i "s/查找字段/替换字段/g" `grep 查找字段 -rl 路径`
    sed -i "s/查找字段/替换字段/g" ./*
```

<!--more-->
倘若字符串中包含“/"等特殊字符串，可以:
```bash
    sed -i "s#查找字段#替换字段#g" `grep 查找字段 -rl 路径`
    sed -i "s#查找字段#替换字段#g" ./*
```    
