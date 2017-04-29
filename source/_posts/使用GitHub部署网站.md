---
title: 使用GitHub部署网站
date: 2017-03-07
categories:
	- 部署
tags:
	- 部署
---

在上一篇博客中介绍了[使用新浪云部署网站](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8%E6%96%B0%E6%B5%AA%E4%BA%91%E9%83%A8%E7%BD%B2%E7%BD%91%E7%AB%99/)这篇博客将介绍另一种部署网站的方式，使用GitHub部署网站。
<!--more-->

## 两种部署网站的方式比较
![](http://img.blog.csdn.net/20161227094654160)

部署网站之前，先要有一个GitHub账号，熟悉一些Git命令，注册GitHub账号和使用git命令可以参考下面的文档，这个文档中介绍的非常详细，我也不做过多的介绍  
**从0开始学习GitHub：**[http://pan.baidu.com/s/1hsn57YO](http://pan.baidu.com/s/1hsn57YO)

注册好GitHub账号并且完善用户信息后可以得到一个下图所示的界面，下图是我的GitHub界面，其中界面中的信息介绍可以参考[从0开始学习 GITHUB 系列之「加入 GITHUB」](http://stormzhang.com/github/2016/05/26/learn-github-from-zero2/)，这篇博客对GitHub界面的信息介绍的非常详细
![](http://img.blog.csdn.net/20161226214844895)

## 下面进入正题，使用GitHub部署网站
**第一步：**单击Repositories，其中Repositories在GitHub上表示的是仓库，在GitHub上每个项目都存放在仓库里，一个仓库保存一个项目
![](http://img.blog.csdn.net/20161226215559693)

**第二步：**单击New按钮
![](http://img.blog.csdn.net/20161226220437338)

**第三步：**单击根据图中的提示填写信息，信息填写完成后单击Create respository按钮创建仓库
![](http://img.blog.csdn.net/20161226221833076)

**第四步：**单击创建好仓库后会自动跳转到下图所示的界面，在界面中单击Settings
![](http://img.blog.csdn.net/20161226222230082)

**第五步：**进入设置界面后一直往下，找到GitHub Page,并且单击GitHub Page模块中的Choose them按钮创建一个网站的主题
![](http://img.blog.csdn.net/20161226222855256)

**第六步：**选择Cayman主题，然后单击select theme按钮
![](http://img.blog.csdn.net/20161226223107905)

**第七步：**单击Commit changes按钮
![](http://img.blog.csdn.net/20161226223508227)

**第八步：**单击Commit changes按钮后会自动跳转到我们创建的仓库界面，里面包含了仓库的各种信息，其中master表示这个仓库位于master分之上，进入界面后单击Settings按钮
![](http://img.blog.csdn.net/20161226224351486)

**第九步：** 在Settings界面中往下滑，滑到GitHub Page模块，可以看到GitHub Page模块中多了一个网址
![](http://img.blog.csdn.net/20161226224724966)

**第十步：**在浏览器中打开网址后可以看到网页上呈现出的内容就是我们刚刚创建的主题为Cayman的网页
![](http://img.blog.csdn.net/20161226225252484)

**第十一步：**回到GitHub上并且打开我们刚刚创建的那个仓库，仓库里的文件就是刚刚在浏览器中显示的内容，接下来要做的事情就是修改仓库里的文件，单击Clone or download按钮
![](http://img.blog.csdn.net/20161226225859038)

**第十二步：**单击复制到剪切板按钮，复制仓库的url
![](http://img.blog.csdn.net/20161226230341481)

**第十三步：**在下面的操作中需要电脑中安装了git，并且熟悉几个简单的git命令，关于git的安装以及git命令的使用可以参考[从0开始学习 GITHUB 系列之「GIT 速成」](http://stormzhang.com/github/2016/05/30/learn-github-from-zero3/)这篇博客将git介绍的非常通俗易懂，安装好git后，先在电脑中创建一个文件夹用于保存从Github中克隆下来的仓库，我建的文件夹叫做GitProject，在E:\game路径下，打开命令行进入GitProject文件夹下
![](http://img.blog.csdn.net/20161226231237026)

**第十四步：**在命令行中执行`git clone https://github.com/meishaxiaozi/boyaa.git`命令，
其中`git clone`表示要克隆一个项目，后面的`https://github.com/meishaxiaozi/boyaa.git`表示项目地址，该地址是由**第十二步**操作获得的，当在最后一行出现了100%表示，远程仓库已经成功的克隆到了本地
![](http://img.blog.csdn.net/20161226231723810)

**第十五步：**打开GitProject文件夹，可以看到在文件夹中多了一个boyaa文件，该文件正是刚刚在GitHub中创建的仓库
![](http://img.blog.csdn.net/20161226232212468)

**第十六步：**打开文件，并且将需要上传到GitHub上的网站添加到该文件中
![](http://img.blog.csdn.net/20161226232503219)

**第十七步：**打开命令行，并且进入boyaa文件夹下，并且执行 `git add .` 命令，此命令表示将需要提交到git中的文件先添加到缓存
![](http://img.blog.csdn.net/20161226232914298)

**第十八步：**执行 `git commit -m “first commit .”`命令，此命令表示将文件提交到git中，下面显示的都是提交到git中的文件
![](http://img.blog.csdn.net/20161226233236959)

**第十九步：**执行 `git push origin master` 命令，将文件push到GitHub上的master分支上，当出现下图所示的提示信息时，表示网站已经成功的提交到了GitHub上
![](http://img.blog.csdn.net/20161226233708442)

**第二十步：**回到Github上的boyaa仓库，可以看到文件已经全部提交上来了
![](http://img.blog.csdn.net/20161226233941249)

**第二十一步：**再次打开位于Settings下，GitHub Page模块中的网址，可以看到网页变成了我们修改后的页面  
**网站的网址：**[https://meishaxiaozi.github.io/boyaa/](https://meishaxiaozi.github.io/boyaa/)  
**网址的格式：**https:// + GitHub的用户名 + .github.io/ + 仓库的名称
![](http://img.blog.csdn.net/20161226235606553)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/使用GitHub部署网站](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8GitHub%E9%83%A8%E7%BD%B2%E7%BD%91%E7%AB%99/)】