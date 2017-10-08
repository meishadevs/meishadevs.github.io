---
title: 常用的Git命令
categories:
  - Git
tags:
  - Git 
date: 2017-04-29 10:18:01
---

整理的一些常用的Git命令
<!--more-->

#### 获得提交代码时的用户名
	git config --global user.name

#### 获得提交代码的邮箱
	git config --global user.email

#### 将提交代码的用户名设置为username
	git config --global user.name username

#### 将提交代码的邮箱设置为email
	git config --global user.email email

#### 查看本地分支
	git branch

#### 查看远程分支
	git branch -r

#### 删除本地分支，其中develop表示分支名称
	git branch -d develop 

#### 强制删除本地分支，其中develop表示分支名称
	git branch -D develop

#### 删除远程分支方法1，其中develop表示远程分支名称
	git push origin :develop

#### 删除远程分支方法2，其中develop表示远程分支名称
	git push origin --delete develop

#### 切换到master分支
	git checkout master 

#### 初始化一个本地Git仓库
	git init

####  查看本地仓库的状态
	git status

#### 将当前目录下的所有文件添加到暂存区
	git add .

#### 将本地暂存文件提交的本地仓库
	git commit -m "update some data"

#### 为本地仓库添加一个远程仓库

	# 添加一个远端地址并起了一个别名叫origin
	git remote add origin https://github.com/username/reponame.git


#### 查看所有的远程仓库
	git remote -v

#### 将本地仓库中master分支上的数据推送到远程仓库的master分支上，如果远程仓库中没有master分支，会在远程创库中自动创建一个master分支
	git push -u origin master

#### 拉取远程仓库上的master分支上的数据到本地仓库
	git pull origin master

#### 回退到某次提交，其中`bbc272`表示提交的哈希值的前六位
	git reset --hard bbc272

#### 查看提交记录
	git log

#### 合并分支，例如将a分支上的代码合并到master分支上，首先切换到master分支，然后执行下面的命令
	git merge a

#### 查看远程分支
	git branch -r

#### 查看代码改动，例如执行下面的Git命令可以查看a.md中代码做了哪些改动
	git diff a.md

#### 强行推送当前分支到远程仓库，即使有冲突，其中branchName表示分支名称
	git push origin branchName --force

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/常用的Git命令/](http://meishadevs.com/blog/%E5%B8%B8%E7%94%A8%E7%9A%84Git%E5%91%BD%E4%BB%A4/)】