---
title: Linux下搭建Java环境
categories:
  - Linux
tags:
  - Linux
date: 2022-05-24 17:02:56
---

这篇文章介绍的是在 Linux 下安装 jdk 1.8 的方法
<!--more-->

###  下载 JDK
访问 jdk 安装包下载的官网 [https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html](https://www.oracle.com/java/technologies/javase/javase8-archive-downloads.html)，进入下载页

在下载页中选择 Linux 64 下的 jdk-8u202-linux-x64.tar.gz 文件，并点击右侧的下载按钮，若没有登录，会跳转到登录页，登录成功后会自动下载
{% img blog-image /images/2022052401.png %}

下载完成后在本地会有一个压缩包，此时 jdk 安装包已经下载到本地了
{% img blog-image /images/2022052402.png %}

### 连接 Linux 服务器
我是使用 FinalShell 连接 Linux 服务器，FinalShell 是一款非常好用的 Linux 管理软件，可以通过访问 [http://www.hostbuf.com/t/988.html](http://www.hostbuf.com/t/988.html) 下载 FinalShell ，连接成功后会显示下图所示的界面
{% img blog-image /images/2022052501.png %}

### 将 JDK 上传到 Linux 服务器

在 /usr/local/  文件目录下创建 java 文件目录

	mkdir /usr/local/java

由于使用命令行创建的文件目录不会更新到 FinalShell，需要选择 /usr/local 文件目录，点击鼠标右键，选择下拉菜单中的刷新，将创建的文件目录同步到 FinalShell
{% img blog-image /images/2022052502.png %}

此时可以看到在 /usr/local 文件目录下多了一个  java 目录
{% img blog-image /images/2022052503.png %}

选择 /usr/local 文件目录 下的 java 目录，并单击鼠标右键，选择下拉菜单中的上传
{% img blog-image /images/2022052504.png %}

选择前面下载的 JDK 压缩包，选择完成后点击窗口中的确定按钮
{% img blog-image /images/2022052505.png %}

等到上传进度提示窗口显示已完，表示 JDK 上传到了 Linux 服务器下
{% img blog-image /images/2022052506.png %}

此可以看到 /usr/local/java 目录下多了一个 JDK 压缩包
{% img blog-image /images/2022052507.png %}

### 解压 JDK
在命令行中执行下面的命令进入 /usr/local/java 目录下

	cd /usr/local/java 

执行下面命令，解压 JDK

	tar -zxvf jdk-8u202-linux-x64.tar.gz

解压完成后，执行下面命令，删除 JDK 压缩 文件

	rm -rf jdk-8u202-linux-x64.tar.gz

执行 ls 命令可以看到 JDK 压缩包已经解压成了一个文件目录
{% img blog-image /images/2022052508.png %}

### 配置环境变量

使用 vim 编辑器 打开 /etc/profile 文件

	vim /etc/profile
	
使用 vim 编辑器打开 /etc/profile 文件的效果
{% img blog-image /images/2022052510.png %}

按住向下的方向键，将光标移动到最底端
{% img blog-image /images/2022052511.png %}

按一下键盘上的 O 键，此时光标会另起一行，最底端会显示 “插入” 的提示文字，表示进入了编辑模式下
{% img blog-image /images/2022052512.png %}

添加 java 配置文件

	export JAVA_HOME=/usr/local/java/jdk1.8.0_202
	export PATH=$JAVA_HOME/bin:$PATH
	export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
	
添加完成后，按一下键盘上的 Esc 键，此时最底端没有任何提示文字，表示退出了编辑模式
{% img blog-image /images/2022052513.png %}

输入 :wq 并按下回车，保存编辑的内容，并关闭 vim 编辑器
{% img blog-image /images/2022052514.png %}

在命令行中执行下面命令，重置系统配置文件

	source /etc/profile
	
### 验证 JDK 是否安装成功

在命令行中执行检测 java 版本的命令

	java -version

当显示了 JDK 版本信息时，表示 JDK 安装成功了
{% img blog-image /images/2022052515.png %}

### 执行 hello world 程序

创建 Demo.java 文件

	touch Demo.java
	
使用 vim 编辑器打开 HelloWorl.java 文件

	vim Demo.java
	
输入 i 键进入编辑模式下，并添加下面的 java 代码

	public class Demo {
		public static void main(String[] args) {
			System.out.println("Hello World");
		}
	}

添加完代码后按一下 Esc 键，退出编辑模式
{% img blog-image /images/2022053001.png %}

输入 :wq 并按一下回车键，保存 Demo.java 文件并关闭 vim 编辑器
{% img blog-image /images/2022053002.png %}

编译 java 代码

	javac Demo.java
	
运行 class

	java Demo
	
此时可以看到控制台中输出了执行结果
{% img blog-image /images/2022053003.png %}

### 参考资料
- [Linux安装JDK1.8教程（2021最新最详细）](https://zhuanlan.zhihu.com/p/343227137)
- [Linux下安装jdk的两种方法](https://www.cnblogs.com/Dr-wei/p/13339957.html)
- [Linux 系统下 JDK 安装和 Java 环境变量配置](https://blog.csdn.net/xietansheng/article/details/84189514)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[Linux下搭建Java环境](http://meishadevs.com/blog/Linux下搭建Java环境)】


