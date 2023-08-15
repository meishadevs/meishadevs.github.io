---
title: Linux下搭建Node.js环境
categories:
  - Linux
tags:
  - Linux
date: 2022-05-30 14:52:49
---

## 搭建环境

### 下载 Node.js 安装包

	wget https://cdn.npmmirror.com/binaries/node/v12.9.0/node-v12.9.0-linux-x64.tar.xz
	
### 解压 Node.js 安装包

	tar -xvf node-v12.9.0-linux-x64.tar.xz
	
### 删除压缩包

	rm -rf node-v12.9.0-linux-x64.tar.xz
	
### 重命名 Node.js 安装目录

	mv node-v12.9.0-linux-x64/ /usr/local/node
	
### 将 Node.js 安装目录添加到环境变量中

	echo "export PATH=$PATH:/usr/local/node/bin" >> /etc/profile
	
### 使配置的 Node.js 环境变量立即生效

	source /etc/profile
	
### 查看 node 的版本

	node -v
	
node 的版本信息
{% img blog-image /images/2022053004.png %}

### 查看 npm 的版本

	npm -v
	
npm 的版本信息
{% img blog-image /images/2022053005.png %}

## 测试 Node.js 环境

创建 HelloWorld.js 文件

	touch HelloWorld.js
	
使用 vim 编辑器打开 HelloWorld.js 文件

	vim HelloWorld.js
	
按下 i 键进入编辑模式下，并添加下面的代码

	var http = require('http');

	http.createServer(function (request, response) {
		response.writeHead(
			200,
			{
				'Content-Type': 'text/plain'
			});
		response.end('Hello World\n');
	}).listen(8080);

	console.log('Server started');
	
按下 Esc 键退出编辑模式，输入 :wq 保存并退出 vim 编辑器

启动 node 服务，运行 HelloWorld.js 文件

	node HelloWorld.js
	
当控制台中显示下图的提示信息时，表示 node 服务启动成功了
{% img blog-image /images/2022053006.png %}

此时在浏览器中访问 [http://139.224.224.231:8080](http://139.224.224.231:8080)，可以看到浏览器上显示了 Hello World，其中 39.224.224.231 为服务器 ip
{% img blog-image /images/2022053007.png %}

## 常用的node命令

    # 查看 Node.js 版本
    node -v
  
    # 查看 npm 版本
    npm -v
  
    # 使用 Node.js 在本地开启一个服务
    npx serve
  
> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[Linux下搭建Node.js环境](http://meishadevs.com/blog/Linux下搭建Node.js环境)】