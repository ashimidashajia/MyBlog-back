---
layout: post
title:  利用清华大学开源镜像下载 Android5.1 源码
categories: Android底层开发
tags: Android底层
date: 2015-09-15 15:36:23
---



---
以前都是从Google的站点下载同步更新的，但是现在有了国内的镜像站点就好多了
清华大学不愧为国内第一名校，我等程序猿也能沾沾光，再也不愁为下载android源码而苦恼了！！
<!--more-->
## 下载repo
1）创建repo目录
```shell
    mkdir ~/bin 
    PATH=~/bin:$PATH
```
2）下载repo
```shell
   git clone git://aosp.tuna.tsinghua.edu.cn/android/git-repo.git/
```
克隆下来后将git-repo中的repo文件拷贝到bin目录
```shell
  cp git-repo/repo ~/bin/
```
3）修改repo文件，设置REPO_URL如下：
```shell
  REPO_URL = 'git://aosp.tuna.tsinghua.edu.cn/android/git-repo'
```

## 初始化repo
1）创建目录
```shell
  mkdir ~/aosp
```
2）初始化repo
```shell
cd ~/aosp 
repo init -u git://aosp.tuna.tsinghua.edu.cn/android/platform/manifest -b android-5.1.0_r3
```

ps:在初始化时，提示需要email验证，使用如下命令：
```shell
    git config --global user.email "you@example.com"
    git config --global user.name "Your Name"
```
##  替换已有的AOSP源代码的remote
如果你之前已经通过某种途径获得了AOSP的源码，但是你希望以后通过TUNA同步，只需要将.repo/manifest.xml中的 

```xml
 <remote  name="aosp"
       fetch=".."
       review="https://android-review.googlesource.com/" />
```
     
改为下面的code即可： 
```xml
 <remote  name="aosp"
       fetch="git://aosp.tuna.tsinghua.edu.cn/android/"
       review="https://android-review.googlesource.com/" />
```
这个方法也可以用来在同步Cyanogenmod代码的时候从TUNA同步部分代码

## 下载源码
```shell
  repo sync 
```
清华镜像源，每个 IP 限制并发数为 4, 请勿使用 repo sync -j8 这样的方式同步。不要贪得无厌哦，我没有开多个线程下载源码！！！
我是一次就下载成功了！！！共计31G。

 




