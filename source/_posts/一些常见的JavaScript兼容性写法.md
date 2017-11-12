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

自己平时总结的一些常用的javaScript兼容性写法
<!--more-->

**1. 获得事件**

	var event = event || window.event;

**2. 阻止事件冒泡**

	var event = event || window.event;

	//阻止事件冒泡
	if (event && event.stopPropagation) {
	    event.stopPropagation();
	} else {
	    event.cancelBubble = true;
	}


**3. 获得点击的某个对象的id**

	var targetId = event.target ? event.target.id : event.srcElement.id;

**4. 阻止事件的默认行为**
	
	//除IE浏览器以外的其他浏览器
	if(event.preventDefault) {

	   event.preventDefault();

	//如果当前的浏览器是IE浏览器
	} else {

	   event.returnValue = false;
	}

**5. 获得浏览器的宽度**

	document.documentElement.clientWidth || document.body.clientWidth;

**6. 获得浏览器的高度**

	document.documentElement.clientHeight || document.body.clientHeight；

**7. 获得水平方向上滚动条到浏览器最左端的距离**  

	document.documentElement.scrollLeft || document.body.scrollLeft

**8. 获得竖直方向上的滚动条到浏览器顶部的距离**
	
	document.documentElement.scrollTop || document.body.scrollTop;

**9. 禁止单击鼠标左键并移动鼠标时拖拽图片方法**

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

**10.当浏览器窗口发生变化时，重新加载整个页面**  

	 //监听浏览器窗口大小是否发生变化
    window.onresize = function () {

        //重新加载当前页面
        location.reload(true);
    }

**11.获得浏览器到显示屏的距离**

	//获得浏览器左端到显示屏左端的距离
    var leftPos = (typeof window.screenLeft == 'number') ?
        window.screenLeft : window.screenX;

    //获得浏览器上端到显示屏上端的距离
    var topPos = (typeof window.screenTop == 'number') ?
        window.screenTop : window.screenY;

**12.获得浏览器窗口大小**

	//获得浏览器窗口的宽度
	var pageWidth = window.innerWidth;

	//获得浏览器窗口的高度
    var pageHeight = window.innerHeight;

    if (typeof pageWidth != 'number') {
        if (document.compatMode == 'CSS1Compat') {
            pageWidth = document.documentElement.clientWidth;
            pageHeight = document.documentElement.clientHeight;
        } else {
            pageWidth = document.body.clientWidth;
            pageHeight = document.body.clientHeight;
        }
    }


> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/一些常见的JavaScript兼容性写法](http://meishadevs.com/blog/%E4%B8%80%E4%BA%9B%E5%B8%B8%E8%A7%81%E7%9A%84JavaScript%E5%85%BC%E5%AE%B9%E6%80%A7%E5%86%99%E6%B3%95/)】