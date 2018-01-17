---
title: 使用Less
date: 2017-03-31
categories:
	- 预处理CSS
	- Less
tags:
	- 预处理CSS
	- Less
---

# 为什么要使用预处理CSS
在使用CSS过程中会遇到一个非常头疼的问题，因为CSS中没有像java/C++或者PHP等程序语言一样有有自己的变量、常量、条件语句以及一些编程语法，只是一行行单纯的属性描述，写起来相当的费事，而且代码难以组织和维护，为了解决这个问题，引入了预处理CSS，预处理CSS可以像Java/C++或者PHP一样用变量，函数等语法描述CSS。
<!--more-->

# 什么是预处理CSS
CSS预处理器用一种专门的编程语言，进行Web页面样式设计，然后再编译成正常的CSS文件，以供项目使用。CSS预处理器为CSS增加一些编程的特性，无需考虑浏览器的兼容性问题，例如你可以在CSS中使用变量、简单的逻辑程序、函数等等在编程语言中的一些基本特性，可以让你的CSS更加简洁、适应性更强、可读性更佳，更易于代码的维护等诸多好处，预处理CSS编程语言有Les，Sass，styuls。

# 为什么使用Less
Less是一款比较流行的预处理CSS，支持变量、混合、函数、嵌套、循环等特点。

# 学习Less的常用网站
**Less官网 [http://lesscss.org/](http://lesscss.org/)**  
**Less中文网 [http://lesscss.cn/](http://lesscss.cn/)**  
**w3cplus [http://www.w3cplus.com/css/less](http://www.w3cplus.com/css/less)**  

# 搭建Less开发环境
### **需要用到的软件**  
**[Node.js](http://nodejs.cn/)**

### 安装Less

	npm install -g less

### 使用Less

**创建Less文件**  
在一个文件夹下新建一个style.less文件，例如我在E:\game\HtmlProject\less下创建了一个style.less文件
![这里写图片描述](http://img.blog.csdn.net/20170326102025941)

**向文件中添加Less代码**
向style.less文件中添加下面的Less代码

	//定义一个变量，用于存放一个颜色
	@mainColor: #e92322;
	
	/* 创建一个body标签的样式 */
	body {
	
	  /*设置body的背景颜色*/
	  background-color: @mainColor;
	}

**将Less文件编译成CSS文件**
打开命令行，并且进入到style.less所在的目录下执行`lessc style.less`命令将Less文件编译成CSS文件，生成的CSS文件会显示在命令行中
![这里写图片描述](http://img.blog.csdn.net/20170326103159306)

**将编译生成的CSS文件保存在本地**
在命令行中执行`lessc style.less > style.css`命令后，会先在style.less文件的同级目录下创建一个style.css文件，并且将编译生成的CSS代码保存在style.css文件中
![这里写图片描述](http://img.blog.csdn.net/20170326103704105)

**查看style.css中的代码**
打开style.css文件后，可以看到style.css中的CSS代码和在命令行中的代码一样
![这里写图片描述](http://img.blog.csdn.net/20170326104523338)

**压缩CSS**
在开发中，为了减少网络请求资源的大小，通常需要压缩CSS文件，Less中提供了一个压缩CSS的插件，先执行`npm install -g less-plugin-clean-css`命令安装插件，然后执行`lessc style.less --clean-css="--s1 --advanced --compatibility=ie8" > style.min.css`命令，执行该命令后首先会将Less代码编译成CSS代码，然后会压缩CSS代码，最后会创建一个style.min.css文件，并且将压缩后的CSS代码保存到style.min.css文件中

**压缩后的CSS代码**
压缩后的CSS代码中删掉了注释和空格，换行等无意义的数据 
`body{background-color:#e92322}`


# Less中的一些其他用法

**Less中实现标签嵌套**
下面的Less代码中container下面存在多重嵌套的标签

	//定义变量，记录container的宽度
	@width: 1000px;
	
	//定义变量，记录container的高度
	@height: 2000px;
	
	//创建变量，记录div的颜色
	@mainColor: #f0f9f0;
	
	/* 嵌套的用法 */ 
	.container {
	  width: @width;
	  height: @height;
	  background-color: #ff0;
	
	  .row {
	    height: 200px;
	
	    div {
	      border-left: 1px solid @mainColor;
	
	       > a {
	        color: red;
	
	        &:hover {
	          color: green;
	        }
	      }
	    }
	  }
	}

编译生成的CSS代码如下
![这里写图片描述](http://img.blog.csdn.net/20170326111954541)

**Less中使用函数**
在下面的代码中body，header，footer标签都要设置border-radius属性，为了减少代码量可以创建一个setRadius函数，让这三个标签都通过调用setRadius函数设置border-radius属性大大的减少了代码量，提高了开发效率

	/**
	 * 为标签设置border-radius属性
	 * @radius 标签的半径
	 * @return 没有返回值
	 */
	.setRadius(@radius: 5px) {
	  -moz-border-radius: @radius;
	  -webkit-border-radius: @radius;
	  border-radius: @radius;
	}
	
	header {
	
		//给header标签设置border-radius属性
		.setRadius;
	}
	
	footer {
		//给footer标签设置border-radius属性
		.setRadius(10px);
	}
	
	body {
		//给body标签设置border-radius属性
		.setRadius(15px);
	}

执行结果
![这里写图片描述](http://img.blog.csdn.net/20170326114125041)

**合并less文件**
在开发中使用less文件的合并功能是一个非常高效且很适合团队开发的方式，比如在一个团队中有三个成员，A成员负责开发页面的header部分，A成员可以建立一个header.less文件，B成员负责开发页面中的banner部分，B成员可以创建一个banner.less文件，C成员负责开发页面中的footer部分，C成员可以建议一个footer.less文件，开发完成后可以将header.less、banner.less、footer.less合并在一个CSS文件中
假定header.less中代码如下

	#header {
		background-color: red;
	}

banner.less中的代码

	#banner {
		background-color: green;
	}

footer.less中的代码

	#footer {
		background-color: blue;
	}

将这三个less文件中的代码合并到style.less中

	//引入header.less文件
	@import url('header.less');
	
	//引入banner.less文件
	@import url('banner.less');
	
	//引入footer.less文件
	@import url('footer.less');

编译index.less文件，编译结果如下，可以看到三个less文件中的代码都编译成了CSS文件，并且放在一起
![这里写图片描述](http://img.blog.csdn.net/20170326120411756)

# 在网页中直接使用Less

## 为什么要在网页中直接使用Less
如果按照上面介绍的方法使用Less，需要每次使用Less写完一点样式后就将Less编译成CSS文件，再在html中引入CSS，总是重复这个操作大大降低了开发效率，为了解决这个问题，可以通过一点简单的配置，可以实现在网页中直接运行
## 配置在网页中直接运行Less的环境
**下载less.js-2.5.1文件**
通过[https://pan.baidu.com/s/1pLM3j6r](https://pan.baidu.com/s/1pLM3j6r)下载less.js-2.5.1.zip文件
![这里写图片描述](http://img.blog.csdn.net/20170327105805389)

**创建项目**
创建一个项目。并且将less.js-2.5.1.zip解压到项目目录下

**创建Less文件**
在项目目录下创建一个main.less文件，并在向main.less中添加如下代码

	//创建变量，用于设置body的宽度
	@width: 1024px;
	
	//创建变量，用于设置body的高度
	@height: 1000px;
	
	//创建变量，用于设置body的背景颜色
	@backgroundColor: #f5f5f5;
	
	body {
	  width: @width;
	  height: @height;
	  margin: 0;
	  padding: 50px;
	  background-color: @backgroundColor;
	}

**创建HTML文件**
在项目目录下创建一个index.html文件，并且向index.html中添加如下代码

	<!DOCTYPE html>
	<html lang="en">
	
	<head>
	  <meta charset="UTF-8">
	  <title>测试网页中直接使用less文件的效果</title>
	  <link rel="stylesheet/less" href="main.less">
	</head>
	
	<body>
	
	  <script src="less.js-2.5.1\dist\less.min.js"></script>
	</body>
	
	</html>

**运行项目**
使用HTTP请求的方式在浏览器中运行index.html文件，WebStrom中点击运行按钮后会自动以HTTP请求的方式在浏览器中运行index.html文件，此时查看console控制台，当console控制台中展示下面的信息，表示项目运行成功
![这里写图片描述](http://img.blog.csdn.net/20170327110802691)

**查看元素信息**
在Elements模块下可以看到为body元素设置了CSS样式，表示Less文件在网页中运行成功
![这里写图片描述](http://img.blog.csdn.net/20170327111130924)

## 特别说明
这种方法只能用于开发测试中，开发完成后需要将Less编译成CSS

## 使用Less做的一个小项目
使用Less实现博雅互动首页 [https://github.com/meishadevs/boyaa](https://github.com/meishadevs/boyaa)

## 参考链接
- [Less快速入门](http://less.bootcss.com/)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/使用Less](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8Less/)】