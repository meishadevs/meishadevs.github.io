---
title: 常见的ES6语法
categories:
  - ES6
tags:
  - ES6
date: 2018-12-17 09:23:40
---

<!--more-->

### 使用箭头函数简化代码

	var obj = {
		typ: Object,
		default: () => ({})
	}
	
上面的代码是下面代码的简写形式

	var obj = {
		type: Object,
		default: function () {
			return {};
		}
	}


### 简化方法的写法

	var obj = {
		create() {
			console.log("调用创建obj对象的方法");
		}
	};

	obj.create();

上面的代码是下面代码的简写形式

	var obj = {
		create: function () {
			console.log("调用创建obj对象的方法");
		}
	};

	obj.create();
	
### 对象合并

下面的代码实现了将obj1对象和obj2对象合并到了一起，并且将合并后的值赋值给obj3

	var obj1 = {
		name: "meishadevs"
	};

	var obj2 = {
		job: "Front-end development"
	};

	var obj3 = Object.assign(obj1, obj2);
	
obj3的值如下
{% img blog-image /images/2018122601.png %}

### 模板语法

	let str1 = 'hello'
    let str2 = 'world'
    let str3 = `${str1} ${str2}`
	
str3的值如下

	hello world

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[常见的ES6语法](http://meishadevs.coding.me/blog/%E5%B8%B8%E8%A7%81%E7%9A%84ES6%E8%AF%AD%E6%B3%95/)】