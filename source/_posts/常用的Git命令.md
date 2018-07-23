---
title: 常用的Git命令
categories:
  - Git
tags:
  - Git 
date: 2017-04-29 10:18:01
---

自己平时总结的一些常用的Git命令
<!--more-->

#### 获得提交代码的用户名
	# --global为可选参数，当在命令中使用--glabal表示所有项目提交代码时都用该用户名，诺不加--global表示只用提交当前项目的代码用该用户名
	git config --global user.name

#### 获得提交代码的邮箱
	# --global为可选参数，当在命令中使用--glabal表示所有项目提交代码时都用该邮箱，诺不加--global表示只用提交当前项目的代码用该邮箱
	git config --global user.email

#### 将提交代码的用户名设置为username
	# --global为可选参数，当在命令中使用--glabal表示所有项目提交代码时都用该用户名，诺不加--global表示只用提交当前项目的代码用该用户名
	git config --global user.name username

#### 将提交代码的邮箱设置为email
	# --global为可选参数，当在命令中使用--glabal表示所有项目提交代码时都用该邮箱，诺不加--global表示只用提交当前项目的代码用该邮箱
	git config --global user.email email

####  下载一个项目和它的整个代码历史到本地  
	git clone url

#### 查看本地分支
	git branch

#### 查看远程分支
	git branch -r

#### 删除本地分支，其中branchName表示本地分支名称
	git branch -d branchName 

#### 强制删除本地分支，其中branchName表示本地分支名称
	git branch -D branchName

#### 删除远程分支方法1，其中branchName表示远程分支名称
	git push origin :branchName

#### 删除远程分支方法2，其中branchName表示远程分支名称
	git push origin --delete branchName

#### 切换到master分支
	git checkout master 

#### 初始化一个本地Git仓库
	git init

####  查看本地仓库的状态
	git status

#### 将当前目录下的所有文件添加到暂存区
	git add .

#### 将暂存区的文件提交到本地仓库
	git commit -m "update some data"

#### 为本地仓库添加一个远程仓库
	git remote add origin https://github.com/username/reponame.git


#### 查看所有远程仓库
	git remote -v

#### 将本地仓库中master分支上的数据推送到远程仓库的master分支上，如果远程仓库中没有master分支，会在远程仓库上自动创建一个master分支
	git push origin master

#### 拉取远程仓库中的master分支上的数据到本地仓库
	git pull origin master

#### 回退到某次提交，其中`bbc272`表示提交的哈希值的前六位
	git reset --hard bbc272

#### 查看提交记录
	git log

#### 合并分支，例如将a分支上的代码合并到master分支上，首先切换到master分支，然后执行下面的命令
	git merge a

#### 查看代码改动，例如执行下面的Git命令可以查看a.md中代码做了哪些改动
	git diff a.md

#### 强行推送当前分支到远程仓库，其中branchName表示分支名称
	git push origin branchName --force

#### 修改远程仓库的url地址，其中url表示远程创库的地址

	git remote set-url origin url

#### 创建一个 a 分支，并且自动切换到 a 分支下
	
	git checkout -b a

#### 把远程分支迁到本地顺便切换到该分支，其中 develop 表示分支名

	git checkout -b develop origin/develop

#### 回退到上一次提交

	git reset --hard HEAD^

#### 解码 base64 编码

	echo base64码 | base64 -d

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[常用的Git命令](http://meishadevs.com/blog/%E5%B8%B8%E7%94%A8%E7%9A%84Git%E5%91%BD%E4%BB%A4/)】