---
title: 使用git提交代码时发生冲突的解决方法
categories:
  - Git
tags:
  - Git
date: 2018-06-06 21:11:25
---
今天是我在项目组中第一次使用Git提交代码，结果一提交就出现了冲突，后来在同事的帮助下终于提交成功了，至于造成冲突的原因是我和同事都在同一个文件中编辑了代码，同事先提交我后提交，同事能正常提交，我提交时就会有冲突，因为Git不明白该保存那个人写的代码，所以就造成了冲突。
<!--more-->

##  制造一个冲突
为了解决冲突，我们首先要制造一个冲突出来，这里我使用GitHub作为远程仓库

**创建一个远程仓库**  
先在GitHub中创建一个远程仓库test，目的就是为了实现向test仓库提交代码时会产生冲突（这里是模拟在我进入项目开发之前我的同事写的项目代码）
{% img blog-image /images/conflict1.png %}

**将远程仓库克隆到本地**  
这里是模拟我进入项目组后拉取项目代码  

	git clone https://github.com/meishadevs/test.git

**打开test文件夹下的README.md文件**  
打开test文件夹下的README.md文件后会看到我在创建远程仓库时创建README.md文件时向README.md文件中写入的一段话“这是一个用于制造冲突的远程仓库”  （这里模拟我看同事写的项目代码）
{% img blog-image /images/conflict2.png %}

**在GitHub上修改README.md文件**  
直接在GitHub上修改README.md文件，将原有的“这是一个用于制造冲突的远程仓库”改成“我是一名程序员”（这里模拟的是我的同事修改项目代码）  
{% img blog-image /images/conflict3.png %}

**在本地修改README.md文件**
将本地test文件中的“这是一个用于制造冲突的远程仓库”改成“我在一个公司从事前端开发”（这里是模拟我修改项目代码）
{% img blog-image /images/conflict4.png %}

**将修改后的代码提交到远程仓库**  

	git add .
	git commit -m "update some data"
	git push origin master

执行将本地修改提交到远程仓库后，会出现一个提交失败的提示信息，这是因为产生了冲突（因为在本地和远程仓库都修改了README.md文件，将本地修改提交到远程仓库时，Git不知道应该保存那个的修改，所以产生了冲突）  
{% img blog-image /images/conflict5.png %}

## 解决冲突

**拉取远程仓库**

	git pull origin master

**确定需要提交的内容**  
再次打开README.md文件会看到MREAMD.md文件中的内容变成了下面的形式

	<<<<<<< HEAD
	我在一个公司从事前端开发
	=======
	我是一名程序员
	>>>>>>> 65fbde5a1555252f5010ce746fcf8ea098500c97

箭头之间的内容表示是出现冲突的内容其中等号上面的内容表示的是我写的，等号下面的内容表示的是我同事写的，根据需要保持一个就可以了，例如此次我要提交我写的内容所以我将README.md中的内容修改如下

	我在一个公司从事前端开发

**再次提交**  

	git add .
	git commit -m "解决冲突"
	git push origin master 
	
这时提交代码时的界面如下表示提交成功了，也表示解决了冲突
{% img blog-image /images/conflict6.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[git中代码冲突的解决方法](http://meishadevs.com/blog/使用git提交代码时发生冲突的解决方法)】