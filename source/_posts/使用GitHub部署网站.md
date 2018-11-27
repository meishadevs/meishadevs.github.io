---
title: 使用GitHub部署网站
date: 2017-03-08
categories:
	- 部署
tags:
	- 部署
---

在上一篇博客中介绍了[使用新浪云部署网站](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8%E6%96%B0%E6%B5%AA%E4%BA%91%E9%83%A8%E7%BD%B2%E7%BD%91%E7%AB%99/)这篇博客将介绍另一种部署网站的方式，使用GitHub部署网站。
<!--more-->

## 两种部署网站的方式比较
{% img blog-image /images/20161227094654160.png %}

部署网站之前，先要有一个GitHub账号，熟悉一些Git命令，注册GitHub账号和使用git命令可以参考下面的文档，这个文档中介绍的非常详细，我也不做过多的介绍  
**从0开始学习GitHub：**[http://pan.baidu.com/s/1hsn57YO](http://pan.baidu.com/s/1hsn57YO)

注册好GitHub账号并且完善用户信息后可以得到一个下图所示的界面，下图是我的GitHub界面，其中界面中的信息介绍可以参考[从0开始学习 GITHUB 系列之「加入 GITHUB」](http://stormzhang.com/github/2016/05/26/learn-github-from-zero2/)，这篇博客对GitHub界面的信息介绍的非常详细
{% img blog-image /images/20161226214844895.png %}

## 下面进入正题，使用GitHub部署网站
**第一步：**单击Repositories，其中Repositories在GitHub上表示的是仓库，在GitHub上每个项目都存放在仓库里，一个仓库保存一个项目
{% img blog-image /images/20161226215559693.png %}

**第二步：**单击New按钮
{% img blog-image /images/20161226220437338.png %}

**第三步：**单击根据图中的提示填写信息，信息填写完成后单击Create respository按钮创建仓库
{% img blog-image /images/20161226221833076.png %}

**第四步：**单击创建好仓库后会自动跳转到下图所示的界面，在界面中单击Settings
{% img blog-image /images/20161226222230082.png %}

**第五步：**进入设置界面后一直往下，找到GitHub Page,并且单击GitHub Page模块中的Choose them按钮创建一个网站的主题
{% img blog-image /images/20161226222855256.png %}

**第六步：**选择Cayman主题，然后单击select theme按钮
{% img blog-image /images/20161226223107905.png %}

**第七步：**单击Commit changes按钮
{% img blog-image /images//20161226223508227.png %}

**第八步：**单击Commit changes按钮后会自动跳转到我们创建的仓库界面，里面包含了仓库的各种信息，其中master表示这个仓库位于master分之上，进入界面后单击Settings按钮
{% img blog-image /images/20161226224351486.png %}

**第九步：** 在Settings界面中往下滑，滑到GitHub Page模块，可以看到GitHub Page模块中多了一个网址
{% img blog-image /images/20161226224724966.png %}

**第十步：**在浏览器中打开网址后可以看到网页上呈现出的内容就是我们刚刚创建的主题为Cayman的网页
{% img blog-image /images/20161226225252484.png %}

**第十一步：**回到GitHub上并且打开我们刚刚创建的那个仓库，仓库里的文件就是刚刚在浏览器中显示的内容，接下来要做的事情就是修改仓库里的文件，单击Clone or download按钮
{% img blog-image /images/20161226225859038.png %}

**第十二步：**单击复制到剪切板按钮，复制仓库的url
{% img blog-image /images/20161226230341481.png %}

**第十三步：**在下面的操作中需要电脑中安装了git，并且熟悉几个简单的git命令，关于git的安装以及git命令的使用可以参考[从0开始学习 GITHUB 系列之「GIT 速成」](http://stormzhang.com/github/2016/05/30/learn-github-from-zero3/)这篇博客将git介绍的非常通俗易懂，安装好git后，先在电脑中创建一个文件夹用于保存从Github中克隆下来的仓库，我建的文件夹叫做GitProject，在E:\game路径下，打开命令行进入GitProject文件夹下
{% img blog-image /images/20161226231237026.png %}

**第十四步：**执行`git clone https://github.com/meishaxiaozi/boyaa.git`命令，其中`git clone`表示要克隆一个项目，后面的`https://github.com/meishaxiaozi/boyaa.git`表示项目地址，该地址是由**第十二步**操作获得的，当在最后一行出现了100%表示，远程仓库已经成功的克隆到了本地
{% img blog-image /images/20161226231723810.png %}

**第十五步：**打开GitProject文件夹，可以看到在文件夹中多了一个boyaa文件，该文件正是刚刚在GitHub中创建的仓库
{% img blog-image /images/20161226232212468.png %}

**第十六步：**打开文件，并且将需要上传到GitHub上的网站添加到该文件中
{% img blog-image /images/20161226232503219.png %}

**第十七步：**打开命令行，并且进入boyaa文件夹下，并且执行 `git add .` 命令，此命令表示将需要提交到git中的文件先添加到缓存
{% img blog-image /images/20161226232914298.png %}

**第十八步：**执行 `git commit -m “first commit .”`命令，此命令表示将文件提交到git中，下面显示的都是提交到git中的文件
{% img blog-image /images/20161226233236959.png %}

**第十九步：**执行 `git push origin master` 命令，将文件push到GitHub上的master分支上，当出现下图所示的提示信息时，表示网站已经成功的提交到了GitHub上
{% img blog-image /images/20161226233708442.png %}

**第二十步：**回到Github上的boyaa仓库，可以看到文件已经全部提交上来了
{% img blog-image /images/20161226233941249.png %}

**第二十一步：**再次打开位于Settings下，GitHub Page模块中的网址，可以看到网页变成了我们修改后的页面  
**网站的网址：**[https://meishadevs.github.io/boyaa/](https://meishadevs.github.io/boyaa/)  
**网址的格式：**https:// + GitHub的用户名 + .github.io/ + 仓库的名称
{% img blog-image /images/20161226235606553.png %}

## GitHub部署网站简化版
上面介绍的步骤比较复杂，熟悉Git命令的话可以使用几条简单的Git命令实现部署

**第一步：**在Git Bash中执行下面的命令，创建一个boyaa文件夹

	mkdir boyaa

**第二步：**将需要部署到GitHub上的文件添加到boyaa文件夹中
{% img blog-image /images/20170429110653556.png %}

**第三步：**进入boyaa文件夹中

	cd boyaa 

**第四步：**初始化一个本地Git仓库

	git init

**第五步：**将需要提交的文件添加到缓存区

	git add .

**第六步：**将文件提交到本地仓库

	git commit -m "update some data"

**第七步：**创建一个gh-pages分支

	git branch gh-pages

**第八步：**切换到gh-pages分支，gh-pages分支是一个比较特殊的分支，网页文件提交到gh-pages分支上，可以通过HTTP协议访问gh-pages分支上的网页文件

	git checkout gh-pages

**第九步：**为本地仓库关联一个远程仓库，其中远程仓库为上一种方法中的第三步创建的boyaa仓库

	git remote add origin https://github.com/meishadevs/boyaa.git

**第十步：**将网页文件提交到远程仓库中的gh-pages分支上

	git push origin gh-pages

**第十一步：**访问网页  
此时可以通过[https://meishadevs.github.io/boyaa](https://meishadevs.github.io/boyaa)访问部署好的网页

**说明：**部署到gh-pages分支上的网页的URL格式为  

	https:// + username.github.io/ + GitHub上的仓库名

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用GitHub部署网站](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8GitHub%E9%83%A8%E7%BD%B2%E7%BD%91%E7%AB%99/)】