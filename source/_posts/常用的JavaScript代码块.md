---
title: 常用的JavaScript代码块
categories:
  - JavaScript
tags:
  - JavaScript
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

	let str1 = 'hello';
	let str2 = 'world';
	let str3 = `${str1} ${str2}`;

	console.log("str3:", str3);

执行结果
{% img blog-image /images/2021052001.png %}

### 数据筛选

	let array = [5, 6, 7, 8, 9, 10];
		
	// 筛选出数组中数值大于 7 的数据
	let arr = array.filter((value) => {
		return value > 7;
	});

	console.log("arr:", arr);

执行结果
{% img blog-image /images/2021052002.png %}
	
### 判断数组中是否存满足条件的数据

	let array = [5, 6, 7, 8, 9, 10];

	// 判断数组元素中是否存在大于 7 的数字
	let result1 = array.some((value) => {
		return value > 7;
	});

	// 判断数组元素中是否存在大于 10 的数字
	let result2 = array.some((value) => {
		return value > 10;
	});

	console.log("result1:", result1);
	console.log("result2:", result2);
	
执行结果
{% img blog-image /images/2021052003.png %}
	
### 判断数组中所有数据是否都满足条件

	let array = [5, 6, 7, 8, 9, 10];

	// 判断数组中是否所有数据都大于 7
	let result1 = array.every((value) => {
		return value > 7;
	});

	// 判断数组中是否所有数据都大于 5
	let result2 = array.every((value) => {
		return value > 4;
	});

	console.log("result1:", result1);
	console.log("result2:", result2);
	
执行结果
{% img blog-image /images/2021052004.png %}

### 使用 forEach 遍历数组

	let array = [2, 4, 6, 8, 10];
	
	array.forEach(item => {
	  console.log('item:', item);
	})
	
执行结果
{% img blog-image /images/2021052005.png %}

### 使用对象展开运算符合并对象

两个对象存在同名的字段时，后面对象的字段值会覆盖前面对象的字段值，这种操作只会将前一个对象的属性赋值给后面对象的属性

	let obj1 = {
	  name: 'meishadevs',
	  age: 25,
	  sex: '男'
	};
	
	let obj2 = {
	  name: '小红',
	  age: 21,
	  sex: '女',
	  hobby: '唱歌'
	};
	
	let obj3 = { ...obj1, ...obj2 };

执行结果
{% img blog-image /images/2019102201.png %}

### 对象解构

使用对象解构获得对象下的属性值

	let person = {
	  name: 'meishadevs',
	  age: 25,
	  hobby: 'Codding'
	};
	
	var { name, age, hobby } = person;
	
	console.log('name:', name);
	console.log('age:', age);
	console.log('hobby:', hobby);

执行结果
{% img blog-image /images/2019102401.png %}

### 格式化对象数组

	let array = [
		{
			productName: '土豆',
			price: 1.5,
		},
		{
			productName: '菠菜',
			price: 2
		},
		{
			productName: '西红柿',
			price: 0.5
		}
	];
	
	let list = array.map(item => {
		item.price += '元/斤';
		return item;
	});
	
	console.log('list:', list);

执行结果
{% img blog-image /images/2019121701.png %}

### 判断数组中是否存在某个元素

	let array = [10, 20, 30, 40, 50];
	let result1 = array.includes(30);
	let result2  = array.includes(100);
	console.log('result1:', result1);
	console.log('result2:', result2);

执行结果
{% img blog-image /images/2019123001.png %}

### 查找数组中的数据

	let cardTypeList = [
	  {
	    name: '身份证',
	    value: 10
	  },
	  {
	    name: '港澳通行证',
	    value: 20
	  },
	  {
	    name: '台胞证',
	    value: 30
	  },
	  {
	    name: '护照',
	    value: 40
	  },
	  {
	    name: '军官证',
	    value: 50
	  },
	  {
	    name: '士官证',
	    value: 60
	  }];
	
	let value = 30;
	
	let cardType = cardTypeList.find(item => {
	  return item.value === value;
	});
	
	console.log('name:', cardType.name);

执行结果
{% img blog-image /images/2019123002.png %}

### 查找数组中元素的下标

	 let cardTypeList = [
	  {
		name: '身份证',
		value: 10
	  },
	  {
		name: '港澳通行证',
		value: 20
	  },
	  {
		name: '台胞证',
		value: 30
	  },
	  {
		name: '护照',
		value: 40
	  },
	  {
		name: '军官证',
		value: 50
	  },
	  {
		name: '士官证',
		value: 60
	  }];

	let value = 30;

	let index = cardTypeList.findIndex(item => {
	  return item.value === value;
	});

	console.log('index:', index);
	
执行结果
{% img blog-image /images/2020102902.png %}

### 将对象数组中的属性组成一个数组

	let array = [
		{
			productName: '土豆',
			price: 1.5,
		},
		{
			productName: '菠菜',
			price: 2
		},
		{
			productName: '西红柿',
			price: 0.5
		}
	];
	
	let list = array.map(item => item.productName );
	
	console.log('list:', list);

执行结果
{% img blog-image /images/2020061201.png %}

### 异步调用

    // 获得用户基本信息的api接口
    export function info() {
      return request({
        url: '/wechat/current',
        method: 'get'
      })
    }
    
    async getUserInfo() {
      try {
      	 // 异步调用api接口
         let result = await info()
      } catch (error) {
        console.log(error.message);
      }
    },
    
    this.getUserInfo();

### 遍历对象

	let object = {
		name: "meishadevs",
		age: 24,
		hobby: "coding",
		job: "Front-end engineer"
	};
	
	for (let name in object) {
		console.log('属性名：', name);
	    console.log('属性值：', object[name]);
	}

执行结果
{% img blog-image /images/2022060701.png %}

### 检测数值中的元素是否完全相同

 	// 判断当前所选的机组是否是相同的机组
    function isAllEqual(array) {
      return !array.some(function(value, index) {
        return value !== array[0]
      })
    }

    let arr1 = [1, 1, 3, 1, 1, 1]
    let arr2 = [1, 1, 1, 1, 1, 1]
    
    let result1 = isAllEqual(arr1)
    let result2 = isAllEqual(arr2)
    
    console.log("arr1 的检测结果：", result1)
    console.log("arr2 的检测结果：", result2)

执行结果
{% img blog-image /images/2020082801.png %}

### 数组去重

    let array = [1, 1, 1, 1, 2, 3, 4, 4, 5, 3];
    let set = new Set(array);
    let arr = Array.from(set);
    
    console.log('去重前的数据：', array);
    console.log("去重后的数据：", arr);

执行结果
{% img blog-image /images/2020090701.png %}

### 将对象的可枚举属性名保存在数组中

	let object = {
	  name: "meishadevs",
	  age: 24,
	  hobby: "codding",
	  job: "Front-end engineer"
	};
	
	let result = Object.keys(object);
	
	console.log("result:", result);

执行结果
{% img blog-image /images/2020092101.png %}

### 将数值类型数据转换成布尔类型数据

	let bool1 = !!5
	let bool2 = !!0
	
	console.log('bool1:', bool1)
	console.log('bool2:', bool2)

执行结果
{% img blog-image /images/2021081001.png %}

### 判断对象是否为空对象

	let obj1 = {}

	let obj2 = {
	  name: 'meishadevs'
	}

	let length1 = Object.keys(obj1).length
	let length2 = Object.keys(obj2).length

	let result1 = length1 ? 'obj1不是空对象' : 'obj1是空对象'
	let result2 = length2 ? 'obj2不是空对象' : 'obj2是空对象'

	console.log(result1)
	console.log(result2)
	
执行结果
{% img blog-image /images/2022011101.png %}

### 获得 Error 对象中的信息

	let error = new Error("Error 对象中的错误信息");

	console.log("error:", error);
	console.log("message:", error.message);

执行结果
{% img blog-image /images/2022052701.png %}

### 使用 try-catch 捕获错误信息

	try {
	  throw new Error("Error 对象中的错误信息");
	} catch (error) {
	  console.log("error:", error);
	  console.log("message:", error.message);
	}

执行结果
{% img blog-image /images/2022052701.png %}

### 将 JavaScript 对象转 JSON 字符串

	var person = {
	  name: 'meishadevs',
	  age: 25,
	  hobby: 'Codding'
	};

	var json = JSON.stringify(person);

	console.log("json:", json);
	
执行结果
{% img blog-image /images/2022061701.png %}

### 将 JSON 字符串转 JavaScript 对象 

	var person = '{"name":"meishadevs","age":25,"hobby":"Codding"}';

	var json = JSON.parse(person);

	console.log("json:", json);
	
执行结果
{% img blog-image /images/2022061702.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[常用的JavaScript代码块](http://meishadevs.com/blog/常用的JavaScript代码块)】
