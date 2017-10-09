---
title: 一些常见的CSS兼容性写法
date: 2017-03-05
categories:
	- CSS
	- 兼容
tags:
    - CSS
    - 兼容
---

积累的一些常见的CSS兼容性写法。
<!--more-->

**1. 设置透明度**

	在IE6中使用 filter: alpha(opacity = 40);
	在其他浏览器中使用 opacity: 0.4;

**2. 设置行高**

	/*\9表示兼容所有的IE浏览器*/  
	line-height: 35px\9;

**3. 清除浮动**

	 .clearfix:after {
	    content: '';
	    height: 0;
	    clear: both;
	    overflow: hidden;
	    visibility: hidden;
	    display: block;
	}

	.clearfix {
	    *zoom: 1;
	}

**4. 禁止用户选择文本**
	
	 -moz-user-select: -moz-none;
    -khtml-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none;
    user-select: none;

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/一些常见的CSS兼容性写法](http://meishadevs.com/blog/%E4%B8%80%E4%BA%9B%E5%B8%B8%E8%A7%81%E7%9A%84CSS%E5%85%BC%E5%AE%B9%E6%80%A7%E5%86%99%E6%B3%95/)】