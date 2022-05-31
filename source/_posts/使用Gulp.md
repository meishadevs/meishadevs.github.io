---
title:  使用Gulp
date: 2017-04-15
categories:
	- Gulp
	- 前端自动化
tags:
	- Gulp
	- 前端自动化
---

# 为什么要使用Gulp
在前端开发中通常需要做，预处理语言的编译、js文件的压缩、css文件的压缩、图片的压缩等一系列工作，而使用Gulp可以自动化的完成这些工作，从而提高网站的开发效率，在我的博客[使用Less](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8Less/)中介绍了将Less文件编译成CSS文件的方法，仔细观察可以看到如果按照博客中介绍的方法，在编译多个Less文件或者编译不同文件夹下的Less文件时需要执行多次Less文件编译命令，而使用Gulp可以一次性完成这些操作
<!-- more -->

# Gulp是什么
Gulp是一个可以自动化完成我们开发过程中大量的重复工作的工具，使用Gulp可以自动化的完成如，预处理语言的编译、js文件的压缩、css文件的压缩、html文件的压缩、图片体积优化等工作

# Gulp的特性
- **易于使用** 通过代码优于配置的策略，Gulp 让简单的任务简单，复杂的任务可管理
- **构建快速** 利用 Node.js 流的威力，你可以快速构建项目并减少频繁的 IO 操作
- **插件高质** Gulp 严格的插件指南确保插件如你期望的那样简洁高质得工作
- **易于学习** 通过最少的 API，掌握 Gulp 毫不费力，构建工作尽在掌握：如同一系列流管道

# Gulp的常用网站
- **Gulp官方网站：**[http://gulpjs.com/](http://gulpjs.com/)  
- **Gulp中文网：**[http://www.gulpjs.com.cn/](http://www.gulpjs.com.cn/)
- **Gulp插件地址：**[http://gulpjs.com/plugins/](http://gulpjs.com/plugins/)
- **Gulp官方API：**[https://github.com/gulpjs/gulp/blob/master/docs/API.md](https://github.com/gulpjs/gulp/blob/master/docs/API.md)
- **Gulp中文API：**[http://www.gulpjs.com.cn/docs/api/](http://www.gulpjs.com.cn/docs/api/)

# Gulp的安装与使用

### Gulp的简单应用
**1. 全局安装Gulp**  

	npm install --global gulp

**2. 创建一个code文件夹，并进入到code文件夹下**  
下面的命令是在Git bash中运行的，运行这几条命令，需要安装Git，没有安装Git的可以在电脑上自己手动创建一个code文件夹，并且进入code文件夹下  

	# 创建code文件夹
	mkdir code

	# 进入code文件下
	cd code 

**3.执行下面的命令创建package.json文件**  

	npm init

在命令行中运行`npm init`命令的时候会出现下图所示的要求用户输入name、version等值，当不清楚这些值的含义的时候，一直按回车键，会自动使用默认值
{% img blog-image /images/20170416094616628.png %}

**4.完成这些操作后会在code文件中会生成一个package.json文件**
{% img blog-image /images/20170416094708660.png %}

**5.打开package.json文件可以看到package.json中记录了一些当前项目的信息**  
**name:** 项目的名称  
**version:** 项目的版本  
**description:** 项目的描述信息  
**main:** 项目的入口函数  
**scripts:** scripts属性是一个对象，里边指定了项目的生命周期个各个环节需要执行的命令  
**author:** 项目的作者  
**license:** 项目的许可证  
**devDependencies:** 项目依赖的插件  
**repository:** 项目资源库

**6.在命令行中执行下面的命令，安装Gulp**  

	npm install --save-dev gulp

**7.创建一个Gulp的主文件gulpfile.js，并且在gulpfile.js中添加下面的代码**
Gulp主文件用于注册任务 
	
	//载入gulp模块
	var gulp = require('gulp');
	
	/**
	 * 注册一个任务
	 * @param 任务名称
	 * @param 自动执行的函数
	 */
	gulp.task('say', function() {
		console.log("hello world !");
	});

**8.使用gulp**  
打开命令行，并且在命令行中执行`gulp say`命令，可以看到在控制台中输出了一句"say hello"表示Gulp安装成功
{% img blog-image /images/20170416101457184.png %}

### 使用Gulp实现一个文件拷贝任务
下面的操作都是在项目中安装了Gulp的情况下进行的，没有安装Gulp可以看前面的**Gulp的安装与使用**中的内容

**1.创建一个src文件夹，并且在src文件夹下创建一个index.html文件**  
在Git Bash中执行下面的命令创建一个src文件夹，并在src文件夹下创建一个index.htmll文件，没有安装Git的可以手动创建

	# 创建src文件夹
	mkdir src 

	# 进入到src文件夹下
	cd src

	# 创建index.html文件
	touch index.html

**2.向index.html中添加HTML代码**

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>Document</title>
	</head>
	<body>
	   <h1>这是一个简单的web页面</h1>		
	</body>
	</html>

**3.创建一个Gulp的主文件gulpfile.js，并且在gulpfile.js中添加下面的代码**

	//载入gulp模块
	var gulp = require('gulp');
	
	//文件拷贝任务
	gulp.task('copy', function() {
	
		//获取src目录下的index.html文件
		gulp.src('src/index.html')
	
		//将index.html拷贝到dist目录中
		.pipe(gulp.dest('dist/'));
	});

**4.在命令行中执行文件拷贝任务，将src目录下的index.html文件拷贝到dist目录下**  

	gulp copy

文件拷贝命令执行完成后可以看到在code目录下自动创建了一个dist文件夹，并且在dist文件夹下自动创建了一个index.html文件，表示文件拷贝任务运行成功
{% img blog-image /images/20170416110116584.png %}

**5.自动执行文件拷贝任务**
在这个文件拷贝任务中，有一个非常大的弊端，就是每次更新index.html中的代码的时候，都要在命令行中执行一次`gulp copy`命令，这样做做了重复性操作，也不符合使用Gulp实现自动化的特点，为了改成自动化执行文件拷贝命令，可以修改gulpfile.js中的代码

	//载入gulp模块
	var gulp = require('gulp');
	
	//文件拷贝任务
	gulp.task('copy', function() {
	
		//获取src目录下的index.html文件
		gulp.src('src/index.html')
	
		//将index.html拷贝到dist目录中
		.pipe(gulp.dest('dist/'));
	});
	
	//监视copy任务
	gulp.task('dist', function() {
	
		//当src目录下的index.html文件发生变化的时候
		//执行copy任务
		gulp.watch('src/index.html', ['copy']);
	});

**6.修改好gulpfile.js中的代码后在命令行中执行下面的命令**

	gulp dist

**6.此时只要修改src文件夹的index.html文件,修改完成后只要一保存，HTML代码就能同时同步到dist文件夹下的index.html中**
{% img blog-image /images/20170416113431492.png %}

### 使用Gulp自动将Less编译成CSS
下面的操作都是在项目中安装了Gulp的情况下进行的，没有安装Gulp可以看前面的**Gulp的安装与使用**中的内容

**1.安装gulp-less插件**
	
	npm install gulp-less --save-dev

**2.创建Less文件**  
在Git Bash中执行下面的命令创建一个less文件夹，并且在less文件夹下创建一个style.less文件，在没有安装Git Bash的情况下可以手动创建

	# 创建less文件夹
	mkdir less 

	# 进入less文件夹中
	cd less

	# 创建style.less文件
	touch style.less

**3.向style.less中添加一段简单的Less代码**
	
	@primary-color: #fff;

	body {
		background-color: @primary-color;
	
		.container {
			width: 1028px;
	
			.row {
				padding: 0 15px;
			}
		}
	}

**4.创建一个Gulp的主文件gulpfile.js，并且在gulpfile.js中添加下面的代码**

	//载入gulp模块
	var gulp = require('gulp');
	var less = require('gulp-less');
	
	//创建一个将Less编译成CSS的任务
	gulp.task('less', function() {
		gulp.src('less/*.less')
		.pipe(less())
		.pipe(gulp.dest('css/'));
	});
	
	//监视less任务
	//当less文件发生变化的时候，会自动将Less转换成CSS
	gulp.task('watchLess', function() {
		gulp.watch('./less/*.less', ['less']);
	});

**5.在命令行中执行下面的命令，启动将Less文件编译成CSS文件的任务**
	
	gulp watchLess

**5.修改less文件夹下的style.less**
打开less文件夹下的style.less文件，并且修改style.less文件，当保存后会自动将style.less文件编译成css文件，并且会自动创建一个css目录，在css目录下自动创建一个style.css文件用于存储生成的CSS代码
{% img blog-image /images/20170417204103113.png %}

## 参考链接
- [gulp.js 中文网](https://www.gulpjs.com.cn/)
- [一点 | gulp教程](http://www.ydcss.com/archives/tag/gulp)
- [Browsersync中文网](http://www.browsersync.cn/)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用Gulp](http://meishadevs.com/blog/使用Gulp)】