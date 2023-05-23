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

	const person = {
	  name: 'meishadevs',
	  age: 25,
	  hobby: 'coding'
	};
	
	const { name, age, hobby } = person;
	
	console.log('name:', name);
	console.log('age:', age);
	console.log('hobby:', hobby);

执行结果
{% img blog-image /images/2019102401.png %}

### 数组解构

使用数组解构的方式获得数组下的元素

	const person = ['meishadevs', 25, 'coding'];

	const [name, age, hobby] = person;

	console.log("name:", name);
	console.log("age:", age);
	console.log("hobby:", hobby);

执行结果
{% img blog-image /images/2023052201.png %}

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
         const { data } = await info();
		 console.log("data:", data);
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

### 数组去重简化写法

	let array = [1, 1, 1, 1, 2, 3, 4, 4, 5, 3];
	let arr = [...new Set(array)]

	console.log('去重前的数据：', array);
	console.log("去重后的数据：", arr);
	
执行结果
{% img blog-image /images/2020090701.png %}

### 对象数组去重

	function uniqueArray(arr) {
	  // 使用累加器遍历原始数组
	  return arr.reduce((acc, current) => {

		// 判断累加器数组中是否存在当前数据
		const isDup = acc.some(item => {

		  // 对象数组去重的条件
		  // 对名字和年龄都相同的对象去重
		  return item.name === current.name && item.age === current.age;
		});

		// 如果累加器数组中不存在当前数据
		if (!isDup) {
		  // 将当前数据添加到累加器数据中
		  acc.push(current);
		}

		// 返回累加器数组
		return acc;
		
		// []：传递给方法的初始值
	  }, []);
	}

	const beforeArray = [
	  { name: 'Mike', age: 18 },
	  { name: 'Jane', age: 19 },
	  { name: 'Jane', age: 20 },
	  { name: 'Bob', age: 20 },
	  { name: 'Jane', age: 20 },
	  { name: 'Mike', age: 18 }
	];

	const afterArry = uniqueArray(beforeArray);

	console.log("去重前的对象数组:", beforeArray);
	console.log("去重后的对象数组:", afterArry);
	
执行结果
{% img blog-image /images/2023032701.png %}

### 将对象的可枚举属性名保存在数组中

	let object = {
	  name: "meishadevs",
	  age: 24,
	  hobby: "coding",
	  job: "Front-end engineer"
	};
	
	let result = Object.keys(object);
	
	console.log("result:", result);

执行结果
{% img blog-image /images/2020092101.png %}

### 将数值类型数据转换成布尔类型数据

	const bool1 = !!5
	const bool2 = !!0
	const bool3 = !!null
	const bool4 = !!undefined
	
	console.log('bool1:', bool1);
	console.log('bool2:', bool2);
	console.log('bool3:', bool3);
	console.log('bool4:', bool4);

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

### JavaScript 对象转 JSON 字符串

	var person = {
	  name: 'meishadevs',
	  age: 25,
	  hobby: 'coding'
	};

	var json = JSON.stringify(person);

	console.log("json:", json);
	
执行结果
{% img blog-image /images/2022061701.png %}

### JSON 字符串转 JavaScript 对象 

	var person = '{"name":"meishadevs","age":25,"hobby":"coding"}';

	var json = JSON.parse(person);

	console.log("json:", json);
	
执行结果
{% img blog-image /images/2022061702.png %}

### Promise 的基本用法

	const num = 0;

	const promise = new Promise((resolve, reject) => {
	  if(num >= 50) {
		resolve("验证成功，num 值大于 50");
	  } else {
		reject(new Error("验证失败，num 值小于 50"));
	  }
	}).then(data => {
	  console.log(data);
	}).catch(error => {
	  console.error(error.message);
	});
	
当 num 是一个小于 50 的值时
{% img blog-image /images/2022070801.png %}

当 num 是一个大于 50 的值时
{% img blog-image /images/2022070802.png %}

### 数组中的数字升序排序

	let array = [40, 100, 1, 5, 25, 10];

	console.log("排序前:", array);

	// 将数组中的数据按照从小到大的顺序排序
	array.sort((a, b) => { 
	  return a - b;
	});

	console.log("排序后:", array);

执行结果
{% img blog-image /images/2022072701.png %}

### 数组中的数字降序排序

	let array = [40, 100, 1, 5, 25, 10];

	console.log("排序前:", array);

	// 将数组中的数据按照从大到小的顺序排序
	array.sort((a, b) => { 
	  return b - a;
	});

	console.log("排序后:", array);

执行结果
{% img blog-image /images/2022072702.png %}

### 数组中的字符升序排序

	let array = ['a', 'g', 'b', 'z', 'y'];

	console.log("排序前:", array);

	// 将数组中的数据按照从小到大的顺序排序
	array.sort((a, b) => { 
	  // 先将字母转换成 Unicode 编码形式，再比较
	  return a.charCodeAt() - b.charCodeAt();
	});

	console.log("排序后:", array);
	
执行结果
{% img blog-image /images/2022081301.png %}

### 数组中的字符降序排序

	let array = ['a', 'g', 'b', 'z', 'y'];

	console.log("排序前:", array);

	// 将数组中的数据按照从小到大的顺序排序
	array.sort((a, b) => { 
	  // 先将字母转换成 Unicode 编码形式，再比较
	  return b.charCodeAt() - a.charCodeAt();
	});

	console.log("排序后:", array);
	
执行结果
{% img blog-image /images/2022081302.png %}

### 数组元素累加

	let array = [40, 100, 1, 5, 25, 10];

	let sum = array.reduce((total, current) => {
	  return total + current;
	});

	console.log("sum:", sum);
	
执行结果
{% img blog-image /images/2022081303.png %}

### 数据累加

	// ...args 使用剩余参数的形式接收传递过来的参数
	// ...args 会将传递过来的参数包裹成一个数组 
	function sum(...args) {
	  const result = args.reduce((total, current) => {
		return total + current;
	  });

	  console.log("args:", args);
	  console.log("result:", result);
	}

	sum(40, 100, 1, 5, 25, 10);
	
执行结果
{% img blog-image /images/2023040301.png %}

### 对象数组分类

	// 原数据结构
	let arr = [
	  {
		name: '广告',
		data: 44
	  },
	  {
		name: '广告',
		data: 223
	  },
	  {
		name: '广告',
		data: 512
	  },
	  {
		name: '商用',
		data: 2
	  },
	  {
		name: '商用',
		data: 52
	  },
	  {
		name: '商用',
		data: 35
	  },
	];

	// 获得 arr 数组中的 name 属性值
	const nameList = [...new Set(arr.map(item => item.name))];

	// 记录转换后的结果
	let result = [];

	// 遍历记录 name 属性值的数组
	nameList.map(name => {
	  let obj = {
		name,
		data: []
	  }

	  arr.map(item => {
		if (item.name === name) {
		  obj.data.push(item.data);
		}
	  });

	  result.push(obj);
	});

	console.log("分类前的数据:", arr);
	console.log("分类后的数据:", result);
	
执行结果
{% img blog-image /images/2022121601.png %}

### 删除对象数组下对象的属性

	let array = [
	  {
		name: 'meishadevs',
		age: 25,
		sex: '男',
		hobby: '爬山'
	  },
	  {
		name: '小红',
		age: 21,
		sex: '女',
		hobby: '唱歌'
	  }
	];

	array.forEach((item) => {
	  delete item.age;
	  delete item.sex;
	});

	console.log("array:", array);
	
执行结果
{% img blog-image /images/2023013101.png %}

### 数组转树

	const sourceData = [
	  { id: 1, parentId: 0, name: '生物' },
	  { id: 2, parentId: 1, name: '动物' },
	  { id: 3, parentId: 1, name: '植物' },
	  { id: 4, parentId: 1, name: '微生物' },
	  { id: 5, parentId: 2, name: '哺乳动物' },
	  { id: 6, parentId: 2, name: '卵生动物' },
	  { id: 7, parentId: 3, name: '种子植物' },
	  { id: 8, parentId: 3, name: '蕨类植物' },
	  { id: 9, parentId: 5, name: '大象' },
	  { id: 10, parentId: 5, name: '海豚' },
	  { id: 11, parentId: 5, name: '猩猩' },
	  { id: 12, parentId: 6, name: '蟒蛇' },
	  { id: 13, parentId: 5, name: '麻雀' }
	]

	/**
	* 将数组转成树
	* @param array
	* @return
	*/
	function arrayToTree(array) {
	  // 存放结果集
	  const result = [];
	  
	  // 用于存储每个节点的引用
	  const map = {}; 

	  // 遍历数组
	  for (const item of array) {
		// 当前数组元素的 id
		const id = item.id;

		// 当前数组元素的父 id
		const parentId = item.parentId;
		
		// 如果当前节点不在 map 中
		if (!map[id]) {
		  // 创建一个新节点
		  map[id] = {
			children: []
		  };
		}

		// 将当前节点合并到 map[id] 上，并更新 children 属性的引用
		map[id] = {
		  ...item,
		  children: map[id]['children']
		};
		
		// 获取当前节点的引用
		const treeItem = map[id]; 
		
		// 如果当前节点是根节点
		if (parentId === 0) {
		   // 将其加入result数组
		  result.push(treeItem);
		  
		// 如果当前节点不是根节点
		} else {
		   // 如果当前节点的父节点不在 map 中
		  if (!map[parentId]) {
			// 创建一个新节点
			map[parentId] = {
			  children: []
			};
		  }

		  // 将当前节点加入其父节点的 children 数组中
		  map[parentId].children.push(treeItem);
		}
	  }
	  
	  // 返回结果集
	  return result; 
	}

	// 调用数组转数方法
	const tree = arrayToTree(sourceData);
  
执行结果

	[
	  {
		"id": 1,
		"parentId": 0,
		"name": "生物",
		"children": [
		  {
			"id": 2,
			"parentId": 1,
			"name": "动物",
			"children": [
			  {
				"id": 5,
				"parentId": 2,
				"name": "哺乳动物",
				"children": [
				  {
					"id": 9,
					"parentId": 5,
					"name": "大象",
					"children": []
				  },
				  {
					"id": 10,
					"parentId": 5,
					"name": "海豚",
					"children": []
				  },
				  {
					"id": 11,
					"parentId": 5,
					"name": "猩猩",
					"children": []
				  },
				  {
					"id": 13,
					"parentId": 5,
					"name": "麻雀",
					"children": []
				  }
				]
			  },
			  {
				"id": 6,
				"parentId": 2,
				"name": "卵生动物",
				"children": [
				  {
					"id": 12,
					"parentId": 6,
					"name": "蟒蛇",
					"children": []
				  }
				]
			  }
			]
		  },
		  {
			"id": 3,
			"parentId": 1,
			"name": "植物",
			"children": [
			  {
				"id": 7,
				"parentId": 3,
				"name": "种子植物",
				"children": []
			  },
			  {
				"id": 8,
				"parentId": 3,
				"name": "蕨类植物",
				"children": []
			  }
			]
		  },
		  {
			"id": 4,
			"parentId": 1,
			"name": "微生物",
			"children": []
		  }
		]
	  }
	]
	
### 树转数组

	const treeData = [
	  {
		"id": 1,
		"parentId": 0,
		"name": "生物",
		"children": [
		  {
			"id": 2,
			"parentId": 1,
			"name": "动物",
			"children": [
			  {
				"id": 5,
				"parentId": 2,
				"name": "哺乳动物",
				"children": [
				  {
					"id": 9,
					"parentId": 5,
					"name": "大象",
					"children": []
				  },
				  {
					"id": 10,
					"parentId": 5,
					"name": "海豚",
					"children": []
				  },
				  {
					"id": 11,
					"parentId": 5,
					"name": "猩猩",
					"children": []
				  },
				  {
					"id": 13,
					"parentId": 5,
					"name": "麻雀",
					"children": []
				  }
				]
			  },
			  {
				"id": 6,
				"parentId": 2,
				"name": "卵生动物",
				"children": [
				  {
					"id": 12,
					"parentId": 6,
					"name": "蟒蛇",
					"children": []
				  }
				]
			  }
			]
		  },
		  {
			"id": 3,
			"parentId": 1,
			"name": "植物",
			"children": [
			  {
				"id": 7,
				"parentId": 3,
				"name": "种子植物",
				"children": []
			  },
			  {
				"id": 8,
				"parentId": 3,
				"name": "蕨类植物",
				"children": []
			  }
			]
		  },
		  {
			"id": 4,
			"parentId": 1,
			"name": "微生物",
			"children": []
		  }
		]
	  }
	];

	function treeToArray(tree) {
	  let array = [];

	  // 遍历树
	  let traverTree = (treeData) => {
		// 遍历数组
		treeData.map(item => {
		  // 如果children属性是一个数组
		  if (item.children && item.children.length) {
			traverTree(item.children);
		  }

		  array.push(item);
		});
	  };

	  traverTree(tree);

	  return array;
	}

	const arr = treeToArray(treeData);

	console.log("arr:", arr);
	
执行结果
{% img blog-image /images/2023032801.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[常用的JavaScript代码块](http://meishadevs.com/blog/常用的JavaScript代码块)】
