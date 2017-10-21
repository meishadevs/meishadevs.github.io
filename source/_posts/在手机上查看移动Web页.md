---
title: 在手机上查看移动Web页
categories:
  - 移动Web
tags:
  - 移动Web
date: 2017-10-21 17:40:54
---

我最近在学习做移动端页面，当做好一个移动端页面后想使用手机查看一下移动端页面在手机上的效果，找了很久才找到一个比较好的方法，特意写这篇文章记录下在手机上查看移动端页面的方法
<!--more-->

## 准备的硬件和软件
- [带有android系统的手机]()
- [数据线]()
- [Node.js](https://nodejs.org/en/download/)
- [Browsersync](http://www.browsersync.cn/)
- [Chrome](http://rj.baidu.com/soft/detail/14744.html?ald)

## 配置环境

##### 注意事项
需要提前在电脑中安装Chrome浏览器，在手机上安装移动版的Chrome浏览器，并且通过数据线将手机和电脑连接，手机要和电脑连接在同一wifi下，并且电脑里要先安装好Node.js，因为下面的操作中有些步骤需要用到Node.js，Node.js的安装方法可以参考我前面写的博客[使用NVM安装Node.js](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8NVM%E5%AE%89%E8%A3%85Node.js/)

##### 第一步：全局安装Browsersync

	npm install -g browser-sync 

##### 第二步：进入移动端页面中index.html所在的文件路径下
![](http://img.blog.csdn.net/20171021182843152))

##### 第三步：运行Browsersync
	
	browser-sync start --server

此时会自动使默认的浏览器打开网页，并且在命令行窗口中会显示四个Url地址，其中上面两个表示当前网页的Url地址下面两个Url地址用于打开Browsersync管理页，在Browsersync管理页中可以控制网页  
![](http://img.blog.csdn.net/20171021184022959)
	
此时在手机上浏览Url[http://192.168.0.102:3000](http://192.168.0.102:3000)就可以在手机上看到这个网页，前提必须使手机和电脑连接在同一wifi下  

##### 第四步：在桌面版Chrome浏览器上查看连接到电脑上的移动设备
打开桌面版的Chreme浏览器，在地址框中输入`chrome://inspect`，在显示的页面上可以查看与电脑连接的移动设备
![](http://oq3pg8pg4.bkt.clouddn.com/pic.png)

##### 第五步：发送网址
在输入框中输入网址[http://192.168.0.102:3000](http://192.168.0.102:3000)，并且单击Open按钮，此时会将网址发送到手机上的Chrom浏览器中，如果此时手机上启动了Chrome浏览器，Chrom浏览器会显示该网址的内容，如果没有启动Chrome浏览器，在启动Chrome浏览器时会自动显示该网站的内容
![](http://oq3pg8pg4.bkt.clouddn.com/pic1.PNG)

#### 第六步：在手机上查看移动端页面
打开手机上的Chrome浏览器，可以看到这个移动端页面
![](http://oq3pg8pg4.bkt.clouddn.com/webwxgetms.png)
> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/在手机上查看移动Web页](http://meishadevs.com/blog/%E5%9C%A8%E6%89%8B%E6%9C%BA%E4%B8%8A%E6%9F%A5%E7%9C%8B%E7%A7%BB%E5%8A%A8Web%E9%A1%B5/)】