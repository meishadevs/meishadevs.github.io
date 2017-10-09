---
title: 一些常见的JavaScript兼容性写法
date: 2017-03-06
categories:
	- JavaScript
	- 兼容
tags:
    - JavaScript
    - 兼容
---

总结一些常见的JavaScript上的兼容性写法
<!--more-->

**1.获得事件**

	var event = event || window.event;

**2.阻止事件冒泡**

	var event = event || window.event;

	//阻止事件冒泡
	if (event && event.stopPropagation) {
	    event.stopPropagation();
	} else {
	    event.cancelBubble = true;
	}


**3.获得点击的某个对象的id**

	var targetId = event.target ? event.target.id : event.srcElement.id;

**4.阻止事件的默认行为**
	
	//除IE浏览器以外的其他浏览器
	if(event.preventDefault) {

	   event.preventDefault();

	//如果当前的浏览器是IE浏览器
	} else {

	   event.returnValue = false;
	}

**5.获得浏览器的宽度**

	document.documentElement.clientWidth || document.body.clientWidth;

**6.获得浏览器的高度**

	document.documentElement.clientHeight || document.body.clientHeight；

**7.获得竖直方向上的滑块到浏览器顶部的距离**
	
	document.documentElement.scrollTop || document.body.scrollTop;

**8. 禁止单击鼠标左键并移动鼠标时拖拽图片方法**

	function imgdragstart() {
        return false;
    }

    //获得所有图片
    var imgs = document.getElementsByTagName('img');

    //遍历图片
    for(var i = 0; i < imgs.length; i++) {

        //禁止单击鼠标左键并移动鼠标时拖拽图片
        imgs[i].ondragstart = imgdragstart;
    }

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/一些常见的JavaScript兼容性写法](http://meishadevs.com/blog/%E4%B8%80%E4%BA%9B%E5%B8%B8%E8%A7%81%E7%9A%84JavaScript%E5%85%BC%E5%AE%B9%E6%80%A7%E5%86%99%E6%B3%95/)】