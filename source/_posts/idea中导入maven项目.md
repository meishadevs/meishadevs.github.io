---
title: idea中导入maven项目
categories: 
  - Java
tags:
  - Java
date: 2018-06-26 19:51:37
---

我们项目组所开发的项目没有做前后端分离，所有开发人员都在同一个项目下编写代码，项目的前端使用jQuery+Layui+GoJS+echarts实现，后端使用的是SSH，因为没做前后端分离再加上后端开发用了maven构建代码，所以每个开发人员的开发工具都是idea，刚接触项目时，因为我是做前端开发，对后端不熟，每次搭建开发环境的时候都要叫后端开发的同事帮忙，经过不断摸索，我现在差不多也能自己独立完成开发环境的配置。
<!--more-->

#### 准备一个maven项目
首先需要准备一个使用maven构建的项目，我这里用cloud-component项目作为演示
{% img blog-image /images/2018062601.png %}

#### 将项目导入到idea中

**启动idea**  
{% img blog-image /images/2018062602.png %}

**选择 Import Project 选项**  
{% img blog-image /images/2018062603.png %}

**选择项目目录下的cloud-pom文件夹，因为cloud-pom文件夹下有个pom.xml文件，pom.xml文件中记录了项目的配置信息，选好后单击OK按钮**  
{% img blog-image /images/2018062604.png %}

**选择项目的构建方式为Maven，选好后单击Next按钮**  
{% img blog-image /images/2018062605.png %}

**此时会弹出一个项目的设置对话框，不用管直接使用默认设置点击Next**  
{% img blog-image /images/2018062606.png %}

**此时会弹出一个对话框，并且会会自动选好一个Maven项目，直接单击Next按钮**  
{% img blog-image /images/2018062607.png %}

**设置JDK，设置好后单击Next按钮**  
{% img blog-image /images/2018062608.png %}

**在弹出的对话框中单击Finish按钮**  
{% img blog-image /images/2018062609.png %}

**此时会进入idea的主界面，并且在idea的底部会出现一个滚动条，并且会不断刷新进度表示在下载项目的依赖**  
{% img blog-image /images/2018062610.png %}

####  配置Spring
**进入idea，并且选择菜单栏上的File**  
{% img blog-image /images/2018062611.png %}

**在弹出的下拉菜单中选择Project Structure**  
{% img blog-image /images/2018062612.png %}

**依次进行以下操作：选择Modules、选择cloud-admin下的Spring、点击对话框上的加号**  
{% img blog-image /images/2018062613.png %}

**首先勾选上cloud-admin下的那两个选择，然后单击OK按钮**  
{% img blog-image /images/2018062614.png %}

**此时可以看到配置好了Spring，最后单击OK按钮完成Spring配置**  
{% img blog-image /images/2018062615.png %}


#### 配置Tomcat
**点击工具栏中，箭头所指的图标**  
{% img blog-image /images/2018062616.png %}

**在弹出的下拉菜单中选择Edit Configurations**  
{% img blog-image /images/2018062617.png %}

**点击弹出的对话框上的加号**  
{% img blog-image /images/201806261800.png %}

**在弹出的下拉菜单中选择Tomcat Server，并在弹出的二级菜单中选择Local表示选择本地的Tomcat**  
{% img blog-image /images/2018062619.png %}

**在弹出的Tomcat配置界面中选择Deployment**  
{% img blog-image /images/2018062620.png %}

**单击加号**  
{% img blog-image /images/2018062621.png %}

**选择下拉菜单中的选择下拉菜单中的Artifact**
{% img blog-image /images/2018062622.png %}

**在弹出的对话框中选择cloud-admin:war exploded，选择完成后单击OK按钮**
{% img blog-image /images/2018062623.png %}

**设置 Application context的值为/clod-admin，设置完成后单击OK按钮**
{% img blog-image /images//2018062624.png %}

**在Tomcat配置界面依次做如下设置：设置Name的值为clod-admin(这里当idea中配置了多个Tomcat时为了区分Tomcat)、设置Tomcat的版本、选择On 'Update' action 的值为 Update classes and resources 设置 On frame deactivation 的值为 Update classes and resources，设置完成后单击OK按钮，此时就配置完成Tomcat**
{% img blog-image /images/2018062625.png %}

**此时单击下图圈出的绿色箭头可以启动Tomcat，并且服务器的连接为http://localhost:8080/cloud-admin/**  
{% img blog-image /images/2018062626.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[idea中导入maven项目](http://meishadevs.com/blog/idea中导入maven项目)】