---
title: 常用的Linux命令
categories:
  - Linux
tags:
  - Linux
date: 2019-05-31 09:43:20
---

整理的一些常用的 linux 命令
<!--more-->

#### 查看当前文件目录下的所有文件

	ls
	
#### 查看根目录下的文件

	ls /
	
#### 查看根目录的详细属性

	ls -ld /
	
#### 查看当前文件目录下所有文件的详细信息
	
	# 可查看文件的文件名、创建时间、操作权限等信息
	ll

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
	
#### 刪除文件夹

	# test 表示文件夹的名称
	rmdir test

#### 创建文件

	# a.md 表示需要创建的文件
	touch test.md
	
#### 回到上一级目录

	cd ..
	
#### 回到根目录

	cd ~
	
#### 查看本机的ip地址

	ifconfig lo0
	
#### 查看局域网ip地址

	ifconfig en0
	
#### 清屏

	clear

#### 安装 wget

	yum -y install wget
	
#### 安装网络工具包

	yum install net-tools -y 
	
#### 查看当前工作目录

	pwd
	
#### 显示 file 文件中的内容

	cat file
	
#### 查看命令行中操作的历史记录

	history
	
#### 将文件传送到 Linux 服务器上
	
	# hello.c 需要上传到 Linux 服务器上的文件
	# root 登录 Linux 服务器的用户名
	# 192.168.10.23 Linux 服务器的 ip 地址
	scp hell.c root@192.168.10.23/root
	
#### 解压文件

	# node-v12.4.0.tar.xz 要解压的文件
	tar -xvf node-v12.4.0.tar.xz
	
#### 查看文件所在的目录

	# 查看 redis 所在的目录
	whereis redis
	
#### 进入 redis 数据库操作界面

	redis-cli

#### 登录 redis 数据库

	# 123456 为登录 redis 数据库的密码
	auth 123456
	
#### 进入 redis 下的某个数据库

	# 5 表示进入 redis 下的第 5 个数据库
	select 5
	
#### 查看 redis 数据库下的所有数据

	keys *

#### 删除 redis 数据库中的数据

	flushall
	
#### 使用 rsa 算法生成秘钥

	ssh-keygen -t rsa

#### 在终端中查看生成的公钥

	cat ~/.ssh/id_rsa.pub

#### 在 vim 中查看生成的公钥

	vim  ~/.ssh/id_rsa.pub
	
#### 检测是否和 github 建立连接

	ssh -T git@github.com

#### 退出 vim

	:wq
	
#### 关闭 Linux 服务器上

	shutdown
	
#### base64 加密

	echo "hello world" | base64
	
#### base64 解密

	echo "aGVsbG8gd29ybGQK" | base64 -d

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[常用的Linux命令](http://meishadevs.com/blog/常用的Linux命令)】