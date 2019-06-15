---
title: 常用的Linux命令
categories:
  - Linux
tags:
  - Linux
date: 2019-05-31 09:43:20
---

自己总结的一些常用的 linux 命令
<!--more-->

#### 查看当前文件夹下的所有文件

	ls

#### 查看某个文件的内容

	# fileName为文件名
	cat fileName

#### 清空终端上的内容

	clear

#### 进入某个文件夹下

	# ~/.ssh 表示文件夹的路径
	cd ~/.ssh

#### 创建文件夹

	# test 表示文件夹的名称
	mkdir test

#### 创建文件夹

	# a.md 表示需要创建的文件
	touch test.md
	
#### 回到上一级目录

	cd ..
	
#### 查看本机的ip地址

	ifconfig lo0
	
#### 查看局域网ip地址

	ifconfig en0
	
> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[常用的Linux命令]()】