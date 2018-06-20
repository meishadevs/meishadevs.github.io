---
title: 《JavaScript高级程序设计》读书笔记
categories:
  - 读书笔记
tags:
  - 读书笔记
  - JavaScript
date: 2017-05-04 11:40:36
---

##### kbit/s
数据传送率的单位.意思是每秒钟多少千字节.比如20Kbit/s就是每秒钟20000个字节.一般上网、下载的速度用这个单位.adsl宽带上网下载速度大概为30-50Kbit/s.

<!--more-->

##### JavaScript的组成
**JavaScript**由**ECMAScript(JavaScript的版本)**、**DOM(文档对象模型)**、**BOM(浏览器对象模型)**三部分组成

##### 开启严格模式的方法
在js脚本的最顶部添加下面一段代码

	"use strict"

##### 创建全局变量的方法
**方法1：**在函数外部定义一个变量，在函数内部使用变量

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
![这里写图片描述](http://oq3pg8pg4.bkt.clouddn.com/20170503113832828.png)  
**第二步：**将余数倒序排列就可以得到18的二进制是10010

##### 将十进制的负数转换成二进制
负数的二进制是用负数的绝对值的补码表示，以计算-18的二进制为例介绍负数的二进制计算方法  
**第一步：**计算-18的绝对值 |-18| = 18  
**第二步：**计算18的二进制 0000 0000 0000 0000 0000 0000 0001 0010  
**第三步：**计算二进制的反码 1111 1111 1111 1111 1111 1111 1110 1101  
**第四步：**将反码加1 1111 1111 1111 1111 1111 1111 1110 1110  
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
常见的引用类型：**Object**、**Array**、**Function**、**RegExp**

##### 构造函数
**构造函数的定义：**构造函数是一种特殊的方法，主要用在创建对象时初始化对象，即为对象成员变量赋初始值，总与new运算符一起使用在创建对象的语句中

**构造函数的特点：**  

- 构造函数的函数名和类名相同
- 构造函数定义时没有返回值
- 构造函数只能用于定义对象时初始化对象  

##### 创建Object实例(对象)的两种方式
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

##### JavaScript中创建对象的方式
**方式1：**使用Object创建对象
	
	var person = new Object();
    person.name = "Nicholas";
    person.age = 29;
    person.job = "Software Engineer";

    person.showName = function () {
        console.log(this.name);
    }

    person.showAge = function () {
        console.log(this.age);
    }

    person.showJob = function () {
        console.log(this.job);
    }

**方式2：**用对象字面量语法创建对象
	
	var person = {
        name: "Nicholas",
        age: 29,
        job: "Software Engineer",

        showName: function () {
            console.log(this.name);
        },

        showAge: function () {
            console.log(this.age);
        },

        showJob: function () {
            console.log(this.job);
        }
    };

**方法3：**用函数封装特定接口创建对象
	
	function createPerson(name, age, job) {
        var o = new Object();
        o.name = name;
        o.age = age;
        o.job = job;

        o.showName = function () {
            console.log(this.name);
        };

        o.showAge = function () {
            console.log(this.age);
        };

        o.showJob = function () {
            console.log(this.job);
        };

        return o;
    }

    var person1 = createPerson("Nicholas", 29, "Software Engineer");
    person1.showName();
    person1.showAge();
    person1.showJob();

    var person2 = createPerson("Greg", 27, "Doctor");
    person2.showName();
    person2.showAge();
    person2.showJob();

**方法4：**使用构造函数创建对象
	
	function Person(name, age, job) {
        this.name = name;
        this.age = age;
        this.job = job;

        this.showName = function () {
            console.log(this.name);
        };

        this.showAge = function () {
            console.log(this.age);
        };

        this.showJob = function () {
            console.log(this.job);
        }
    }

    var person1 = new Person("Nicholas", 29, "Software Engineer");
    person1.showName();
    person1.showAge();
    person1.showJob();

    var person2 = new Person("Greg", 27, "Doctor");
    person2.showName();
    person2.showAge();
    person2.showJob();

**方法5：**使用构造函数创建对象改进版
	
	function Person(name, age, job) {
        this.name = name;
        this.age = age;
        this.job = job;

        this.showName = new Function("console.log(this.name)");
        this.showAge = new Function("console.log(this.age)");
        this.showJob = new Function("console.log(this.job)");
    }

    var person1 = new Person("Nicholas", 29, "Software Engineer");
    person1.showName();
    person1.showAge();
    person1.showJob();

    var person2 = new Person("Greg", 27, "Doctor");
    person2.showName();
    person2.showAge();
    person2.showJob();

**方法6：**将成员函数放在外面
	
	function Person(name, age, job) {
        this.name = name;
        this.age = age;
        this.job = job;
        this.showName = showName;
        this.showAge = showAge;
        this.showJob = showJob;
    }

    function showName() {
        console.log(this.name);
    }

    function showAge() {
        console.log(this.age);
    }

    function showJob() {
        console.log(this.job);
    }

    var person1 = new Person("Nicholas", 29, "Software Engineer");
    person1.showName();
    person1.showAge();
    person1.showJob();

    var person2 = new Person("Greg", 27, "Doctor");
    person2.showName();
    person2.showAge();
    person2.showJob();

**方式7：**使用原型创建对象
	
	 function Person() {
    }

    Person.prototype.name = "Nicholas";
    Person.prototype.age = 29;
    Person.prototype.job = "Software Engineer";

    Person.prototype.showName = function () {
        console.log(this.name);
    }

    Person.prototype.showAge = function () {
        console.log(this.age);
    }

    Person.prototype.showJob = function () {
        console.log(this.job);
    }

    var person1 = new Person();
    person1.showName();
    person1.showAge();
    person1.showJob();

##### js中获得父节点下所有子节点的方法  
**childNodes：** 获得的子节点中包含文本节点  
**children:** 获得的子节点中不包含文本节点

##### let、var、const 三者的区别  
**var：** 使用var声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象  
**let：** 使用let声明的变量，其作用域为该语句所在的代码块内，不存在变量提升  
**const：** 使用const声明的是常量，在后面出现的代码中不能再修改该常量的值

##### 属性的描述符
**Configurable：**表示能否通过delete删除属性，从而重新定义属性，能否修改属性的特性，或者能否把属性修改为访问器属性，它的默认值是true  
**Enumerable：**表示能否通过 for-in 循环返回属性，它的默认值是true  
**Writable：**表示能否修改属性的值，它的默认值是true  
**Value：**属性的值

##### 访问器属性的特性
**Configurable：**表示能否通过delete删除属性，从而重新定义属性，能否修改属性的特性，或者能否把属性修改为访问器属性，它的默认值是true  
**Enumerable：**表示能否通过 for-in 循环返回属性，它的默认值是true  
**Get：**在读取属性时调用的函数，默认值为undefined  
**Set：**在写入属性时调用的函数，默认值为undefined

##### target 与 currentTarget
**target：**返回触发事件的那个节点，即事件最初发生的节点  
**currentTarget：**返回事件当前所在的节点，即正在执行的监听函数所绑定的那个节点

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[《JavaScript高级程序设计》读书笔记](http://meishadevs.com/blog/《JavaScript高级程序设计》读书笔记/)】