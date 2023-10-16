---
title: github
author: R package build
date: '2023-10-16'
slug: []
categories: []
tags: 
  - 工具
lastmod: '2023-10-16T18:07:30+08:00'
keywords: []
description: ''
comment: no
toc: no
autoCollapseToc: no
postMetaInFooter: no
hiddenFromHomePage: no
contentCopyright: no
reward: no
mathjax: no
mathjaxEnableSingleDollar: no
mathjaxEnableAutoNumber: no
hideHeaderAndFooter: no
flowchartDiagrams:
  enable: no
  options: ''
sequenceDiagrams:
  enable: no
  options: ''
---

<!--more-->

# git

参考资料

https://zhuanlan.zhihu.com/p/30044692

## 1. 创建本地仓库

### 初始化仓库

方式1： 在Rstudio里建立项目的时候，点击创建git目录，即可直接初始化目录

方式2： 在创建的文件里

```shell
mkdir Rcourse_test
cd Rcourse_test
git init Rcourse_test
```

### 提交目录文件至本地仓库

```shell
git add *   #将test目录下所有文件添加到暂存区

git commit -m "init file"  # 把文件提交仓库（当前分支）

git status # 查看提交情况

```

## 2. 将本地仓库上传至远程仓库

### 设置SSH KEY

**本地添加SSH KEY**

```shell
cd ~/.ssh

# 设置git的用户名和邮箱
git config --global user.name "***************"
git config --global user.email ***************

# 创建秘钥，这个-C 是添加描述，成功后会生成id_rsa  id_rsa.pub两个文件
ssh-keygen -t rsa -C "***************"
```

**github添加SSH KEY**

打开github网址，打开设置，点击ssh设置，点击添加SSH KEY

将 id_rsa.pub文件里的所有内容复制到 Key输入框里



### 额外设置

按照github官方设置ssh key的进行设置后，发现在进行git push时候任然需要输入账号和密码。
可能的问题在于一开始进行git clone时候是使用https进行克隆

```shell
# 使用以下命令查看origin使用的是https还是ssh
git remote -v

# 如果使用的是https替换为ssh方式即可
git remote set-url origin git@github.com:name/repo
```



### 上传本地仓库至远程仓库

```shell
pwd   # Rcourse_test文件夹里

#本地仓库与远程仓库进行关联
git remote add origin git@github.com/luoboqingcai81/Rcourse_test.git

#本地仓库切换至main分支
git branch -M main

# 将本地仓库main分支推送至远程仓库
git push -u origin main
```

