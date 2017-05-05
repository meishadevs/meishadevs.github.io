---
title: 《JavaScript高级程序设计》读书笔记
categories:
  - 读书笔记
tags:
  - 读书笔记
  - JavaScript
date: 2017-05-04 11:40:36
---

最近在做一个电商网站，做到后面坑越挖越大，感觉自己力不从心，所以决定先暂停电商网站项目，好好静下心来看书，在网上看到《JavaScript高级程序设计》是前端必读的书，所以决定先看这本书，以下记录的是阅读时做的笔记。
<!--more-->

##### kbit/s
数据传送率的单位.意思是每秒钟多少千字节.比如20Kbit/s就是每秒钟20000个字节.一般上网、下载的速度用这个单位.adsl宽带上网下载速度大概为30-50Kbit/s.

##### JavaScript的组成
**JavaScript**由**ECMAScript(JavaScript的版本)**、**DOM(文档对象模型)**、**BOM(浏览器对象模型)**三部分组成

##### 开启严格模式的方法
在js脚本的最顶部添加下面一段代码

	"use strict"

##### 创建全局变量的方法
**方法1：**在函数外部定义一个变量，在函数内部调用变量

	var message;

	function test() {
		message = "hello world";
	}

	test();
	alert(message);

**方法2：**在函数内部定义变量，并且不写**var**操作符

	function test() {
		message = "hello world";
	}

	test();
	alert(message);

##### 将十进制转换成二进制的方法
除二取余，倒序排列。例如将十进制的18转换成二进制  
**第一步：**计算除二取余  
![这里写图片描述](http://img.blog.csdn.net/20170503113832828)  
**第二步：**将余数倒序排列就可以得到18的二进制是10010

##### 将十进制的负数转换成二进制
负数的二进制是用负数的绝对值的补码表示，以计算-18的二进制为例介绍负数的二进制计算方法  
**第一步：**计算-18的绝对值 |-18| = 18  
**第二步：**计算-18的绝对值的二进制 0000 0000 0000 0000 0000 0000 0001 0010  
**第三步：**计算二进制的反码 1111 1111 1111 1111 1111 1111 1110 1101  
**第四步：**将反码加1的值为 1111 1111 1111 1111 1111 1111 1110 1110  
**所以-18的二进制值** 1111 1111 1111 1111 1111 1111 1110 1110，其中第31位表示的是符号位不参与计算，1表示是负数，0表示是正数，位的顺序是从右往左排列的从0开始，也就是所最右边的哪位是第0位，然后往左依次是1、2、3、......位以此类推，最后一位是第31位

##### 计算按位非操作的简便方法
操作数的负值减1，例如计算25的按位非操作的方法如下

	var num1 = 25;
	var num2 = -num1 - 1;

##### 获得变量的基本数据类型
JavaScript中使用**typeof**关键字获得变量的基本数据类型
	
	 var s = "Nicholas";
    var b = true;
    var i = 22;
    var u;
    var n = null;
    var o = new Object();

    alert(typeof s);  //string
    alert(typeof i);  //number
    alert(typeof b);  //boolean
    alert(typeof u);  //undefined
    alert(typeof n);  //object
    alert(typeof o);  //object

##### 判断变量的引用的数据类型
JavaScript中使用**instanceof**关键字判断变量的引用数据类型
	
	 var person = new Object();
    var colors = [];
    var pattern = new RegExp();

    alert(person instanceof Object);   //变量person是Object类型吗
    alert(colors instanceof Array);    //变量colors是Array类型吗
    alert(pattern instanceof RegExp);  //变量pattern是RegExp类型吗

##### JavaScript的基本数据类型
JavaScript一共有5种基本数据类型，分别是**Undefined**、**Null**、**Boolean**、**Number**和**String**。

##### JavaScript中的引用类型
常见的引用类型：**Object**、**Array**、

##### 构造函数
**构造函数的定义：**构造函数是一种特殊的方法 主要用来在创建对象时初始化对象 即为对象成员变量赋初始值,总与new运算符一起使用在创建对象的语句中

**构造函数的特点：**  

- 构造函数的函数名和类名相同
- 构造函数定义时没有返回值
- 构造函数只能用于定义对象时初始化对象

####创建Object实例(对象)的两种方式
**方式1：**使用new操作符后跟Object构造函数
	
	var person = new Object();
    person.name = "Nicholas";
    person.age = 29;

**方式2：**使用对象字面量表示法
	
	 var person = {
        name : "Nicholas",
        age : 29
    };

##### 创建数组的方式
**方式1：**使用Array的构造函数创建数组

	//创建一个空数组
    var colors = new Array();

    //创建一个保存20个数据的数组
    var colors = new Array(20);

    //创建一个保存了3个字符串的数组
    var colors = new Array("red", "blue", "green");

**方式2：**使用Array的构造函数创建数组时也可以省略**new**操作符

	 //创建一个空数组
    var colors = Array();

    //创建一个保存20个数据的数组
    var colors = Array(20);

    //创建一个包含3个字符串的数组
    var colors = Array("red", "blue", "green");

**方式3：**使用数组的字面量创建数组
	
	 //创建一个空数组
    var colors = [];

    //创建一个包含3个字符串的数组
    var colors = ["red", "blue", "green"];

##### 栈与队列
**栈的访问规则：**先进后出  
**队列的访问规则：**先进先出

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/《JavaScript高级程序设计》读书笔记/](http://meishadevs.com/blog/《JavaScript高级程序设计》读书笔记/)】