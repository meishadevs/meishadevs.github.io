---
title: 使用NVM安装Node.js
date: 2017-03-11
categories:
	- NVM
	- Node.js
tags:
	- NVM
	- Node.js
---
## 为什么使用NVM安装Node.js
NVM 可以很方便管理 Node.js 的版本，并实现不同 Node.js 版本之间的切换
<!--more-->

## 需要准备的工具
在 [https://pan.baidu.com/s/1gfxajPT](https://pan.baidu.com/s/1gfxajPT) 中下载 NVM 安装包，通过我提供的地址下载的 NVM 安装包，安装包中提供了几个不同版本的 Node.js，当安装包中的 Node.js 版本不能满足需要时，可以向 NVM 中添加更高版本的 Node.js

##  安装NVM
### 下载NVM安装包
将NVM安装包下载下来后放在一个没有空格的全英文路径下，我将NVM放在F:\develop下面
{% img blog-image /images/20170311184329294.png %}

### 解压NVM.zip文件
将nvm.zip文件解压到当前目录下
{% img blog-image /images/20170311222822917.png %}

### 打开nvm文件夹
打开nvm文件夹后，可以看到nvm文件夹中有如下图所示的文件
{% img blog-image /images/20170311224908864.png %}

### 创建settings.txt文件
在nvm文件夹下新建一个settings.txt文件，并且在settings.txt文件中添加下图所示的内容

**内容介绍:**
 **root: F:\develop\nvm** nvm所在的目录
 **path: F:\develop\nodejs** node.js所在的目录
 **arch: 64 ** 当前的操作系统是64位**(诺操作系统是32位此处arch的值应该设为32)**
 **proxy: none** 设置代理服务器，此处不需要设置代理服务器，所以设为none
{% img blog-image /images/20170313214811350.png %}

### 配置环境变量
在环境变量中创建下面的环境变量

	nvm所在的目录
	NVM_HOME = F:\develop\nvm 
	
	Node.js所在的目录
	NVM_SYMLINK = F:\develop\nodejs

将这两个环境变量添加到path中

	%NVM_HOME%;%NVM_SYMLINK%;

### 判断nvm环境变量是否配置成功
打开命令行窗口，在命令行窗口中输入`nvm`命令，当命令行窗口中显示下图中的提示信息，表示nvm环境变量配置成功
{% img blog-image /images/20170313221236424.png %}

### 在命令行窗口中显示NVM中的Node.js
打开命令行窗口，并且输入`nvm ls`命令，命令的执行结果如下图所示，其中图中的5.6.0和4.3.0表示nvm中存在的Node.js的版本
{% img blog-image /images/20170313223355075.png %}

### 使用Node.js
在命令行中输入`nvm use 5.6.0`表示使用版本为5.6.0的Node.js
{% img blog-image /images/20170313223835156.png %}

### 查看当前正在使用的Node.js的版本
输入`nvm ls`命令可以查看当前正在使用的Node.js的版本，星号在那个版本号上就表示当前正在使用的是那个版本的Node.js
{% img blog-image /images/20170313224246892.png %}

### 检查Node.js是否安装
打开文件管理器，转到F:\develop目录下，可以看到目录中多了一个node.js的快捷方式，表示node.js已经安装成功，其中这个目录是由前面操作步骤中配置的path值设置而来的
{% img blog-image /images/20170313224921253.png %}

### 检测Node.js的版本
在命令行中执行`node -v`命令可以查看当前Node.js的版本
{% img blog-image /images/20170313225245161.png %}

### 在命令行中运行javaScript代码
打开命令行，输入`node`命令会进入一个命令行版的代码编辑界面，在命令行中输入一段简单的代码，当输入`console.log("Hello World !");`并且按下回车后，就可以通过Node.js在命令行中执行这段简单的js代码
{% img blog-image /images/20170313230627715.png %}

### 在命令行中运行本地文件中的js代码
在F:\develop下创建一个hello.js文件并且在文件中添加一段简单的代码`console.log("hello worl !");`,打开命令行，并且进入F:\develop目录下，执行`node hello.js`命令便可以运行hello.js中的代码
{% img blog-image /images/20170313231516719.png %}

## 向NVM中添加Node.js
nvm安装包中只提供了两个版本比较老的node.js，若要在nvm中使用新版本的node.js包，可以向nvm文件夹中添加新版本的node.js

### 下载新版 Node.js
首选进入[Node.js下载页](https://nodejs.org/zh-cn/download)
{% img blog-image /images/2023052501.png %}

在写这篇博客时，Node.js 的最新版为 18.16.0，这里以下载 18.16.0 版的 Node.js 为例，选择 Windows 二进制文件，这里根据操作系统的版本选择下载 32 位或 64 位
{% img blog-image /images/2023052502.png %}

本人电脑的操作系统是 64 位的，选择下载 64 位的版本，下载下来后本地会得到一个压缩包
{% img blog-image /images/2023052503.png %}

将压缩包解压，并放在 nvm 目录下
{% img blog-image /images/2023052504.png %}

修改文件夹名称，使其名称更有意义
{% img blog-image /images/2023052505.png %}

### 使用新版 Node.js 
进入命令行下，输入 nvm ls 命令后可以看到新版 Node.js 已经添加到了 nvm 中
{% img blog-image /images/2023052506.png %}

在命令行中执行 nvm use 18.16.0 表示当前使用 18.16.0 版本的 Node.js
{% img blog-image /images/2023052507.png %}

再次进入命令行中，执行 nvm ls 命令后可以看到星号移动到了 18.16.0 的版本上，表示当前使用的是最新的 18.16.0
{% img blog-image /images/2023052508.png %}

在命令行中执行 node -v 命令，可以进一步说明前使用的是最新的 18.16.0
{% img blog-image /images/2023052509.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用NVM安装Node.js](http://meishadevs.com/blog/使用NVM安装Node.js)】