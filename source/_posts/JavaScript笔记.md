---
title: JavaScript笔记
date: 2017-03-06
categories:
	- JavaScript
tags:
    - JavaScript
---

记录了一些常用的JavaScript用法
<!--more-->

### 获得事件

	var event = event || window.event;

### 阻止事件冒泡

	var event = event || window.event;
	
	//阻止事件冒泡
	if (event && event.stopPropagation) {
	    event.stopPropagation();
	} else {
	    event.cancelBubble = true;
	}


### 获得点击的某个对象的id

	var targetId = event.target ? event.target.id : event.srcElement.id;

### 阻止事件的默认行为
	
	//除IE浏览器以外的其他浏览器
	if(event.preventDefault) {
	
	   event.preventDefault();
	
	//如果当前的浏览器是IE浏览器
	} else {
	
	   event.returnValue = false;
	}

### 获得浏览器的宽度

	document.documentElement.clientWidth || document.body.clientWidth;

### 获得浏览器的高度

	document.documentElement.clientHeight || document.body.clientHeight；

### 获得水平方向上滚动条到浏览器最左端的距离

	document.documentElement.scrollLeft || document.body.scrollLeft

### 获得竖直方向上的滚动条到浏览器顶部的距离
	
	document.documentElement.scrollTop || document.body.scrollTop;

### 禁止单击鼠标左键并移动鼠标时拖拽图片方法

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

### 当浏览器窗口发生变化时，重新加载整个页面

	 //监听浏览器窗口大小是否发生变化
	window.onresize = function () {
	
	    //重新加载当前页面
	    location.reload(true);
	}

### 获得浏览器到显示屏的距离

	//获得浏览器左端到显示屏左端的距离
	var leftPos = (typeof window.screenLeft == 'number') ?
	    window.screenLeft : window.screenX;
	
	//获得浏览器上端到显示屏上端的距离
	var topPos = (typeof window.screenTop == 'number') ?
	    window.screenTop : window.screenY;

### 获得浏览器窗口大小

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

### 获得竖直方向上的滚动条到浏览器顶部的距离

	getScrollTop: function () {
	
	    var scrollPos;
	
	    if (window.pageYOffset) {
	
	      scrollPos = window.pageYOffset;
	
	    } else if (document.compatMode && document.compatMode !== 'BackCompat') {
	
	      scrollPos = document.documentElement.scrollTop;
	
	    } else if (document.body) {
	
	      scrollPos = document.body.scrollTop;
	    }
	
	    return scrollPos;
	  }

### 将字符串转换成数组

	var arr = Array.prototype.slice.call('abc');

### 判断数据类型

	var type = function (o) {
	  var s = Object.prototype.toString.call(o);
	  return s.match(/\[object (.*?)\]/)[1].toLowerCase();
	};
	
	type({}); // "object"
	type([]); // "array"
	type(5); // "number"
	type(null); // "null"
	type(); // "undefined"
	type(/abcd/); // "regex"
	type(new Date()); // "date"

### 获得任意范围内数字的随机数

	function getRandomInt(min, max) {
	  return Math.floor(Math.random() * (max - min + 1)) + min;
	}
	
	getRandomInt(1, 6) // 5

### 使用 JavaScript 创建二维数组

	var array = new Array(15);
	
	for (var x = 0; x < 15; x++) {
	    array[x] = new Array(15);
	    for (var y = 0; y < 15; y++) {
	        array[x][y] = 0;
	    }
	}

### 任意值转换成  Base64 编码

	btoa('hello world')

### Base64 编码转成原来的值

	atob('aGVsbG8gd29ybGQ=')

### 使用数组的形式访问对象的属性

	let person = {
	  name: 'meishadevs',
	  age: 25,
	  sex: '男'
	}

	let name = person['name']
	let age = person['age']
	let sex = person['sex']

	console.log('name:', name)
	console.log('age:', age)
	console.log('sex:', sex)
	
执行结果
{% img blog-image /images/2019102901.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[JavaScript笔记]([http://meishadevs.com/blog/JavaScript%E7%AC%94%E8%AE%B0/](http://meishadevs.com/blog/JavaScript笔记/))】