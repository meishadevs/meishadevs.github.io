---
title: 一些有趣的CSS样式 
date: 2017-03-05
categories:
	- CSS
tags:
    - CSS
---

自己平时整理的一些有趣的CSS样式
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

**5. 使用绝对定位将子元素元素的宽度设为父元素宽度的100%，将子元素的高度设为父元素高度的100%**
	
	 position: absolute;
     left: 0;
     right: 0;
     top: 0;
	 bottom: 0;

**6. 使用绝对定位加CSS3中的transform将子元素设置到父元素的正中间**
	
	-webkit-transform: translate(-50%, -50%);
    -moz-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    -o-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
    position: absolute;
    left: 50%;
    top: 50%;

**7. 隐藏溢出标签中的文本并且在标签最后增加一个省略号**

	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/一些常见的CSS兼容性写法](http://meishadevs.com/blog/%E4%B8%80%E4%BA%9B%E5%B8%B8%E8%A7%81%E7%9A%84CSS%E5%85%BC%E5%AE%B9%E6%80%A7%E5%86%99%E6%B3%95/)】