---
title: Vue.js学习笔记
categories:
  - Vue.js
tags:
  - Vue.js

date: 2017-12-01 16:14:29
---

#### 在执行 npm run dev 命令的时候出现8080端口被占用
	在任务管理器中手动结束所有Node.exe进程
<!-- more -->

#### 使用v-for指令遍历组件时产生警告，提示需要在组件上增加一个key属性
	当使用v-for指令遍历组件时，需要在组件上添加一个key属性
	<router-link to="/select" v-for="content in item.classContent" :key="content.id">{{ content }}</router-link>

#### 使用Head标签命名组件报错
	不能使用标签名作为组件名

#### 执行npm run build命令构建Vue.js项目后，在浏览器中打开生成的HTML文件，网站资源文件的路径错误
进入项目目录下的`config/index.js`文件中的`build`对象下的`assetsPublicPath`属性，将`assetsPublicPath`属性的值由 `assetsPublicPath: '/'`，改成 `assetsPublicPath: './'`

#### 执行npm run build命令构建Vue项目后，生成的CSS文件中background url()图片路径错误

需要单独为 css 配置 publicPath   
ExtractTextWebpackPlugin 提供了一个 options.publicPath 的 api，可以为css单独配置 publicPath 

对于用 vue-cli 生成的项目，dist 目录结构如下：

	dist
	├── index.html
	└── static
    ├── css
    ├── img
    └── js

经常遇见的问题是 css 中 background-image 的相对路径不能正确的引用到 img 文件夹中。但是用 ExtractTextWebpackPlugin 的 publicPath 配置就可以。

更改 `build/utils.js` 文件中 ExtractTextPlugin 插件的options 配置：

    if (options.extract) {
      return ExtractTextPlugin.extract({
        use: loaders,
        publicPath: '../../', //注意配置这一部分,根据目录结构自由调整
        fallback: 'vue-style-loader'
      })
    } else {
      return ['vue-style-loader'].concat(loaders)
    }

最后附上 [extract-text-webpack-plugin](https://github.com/webpack-contrib/extract-text-webpack-plugin/blob/master/README.md) 的文档。

#### 修改props属性中的值报错

不能在组件中直接修改props属性中的值，可以通过引入一个中间变量修改prps中的值

	 export default {
	
	    //获取从父组件中传递过来的数据
	    props: ["curPage"],
	
	    data() {
	      return {
	
	        //引入一个中间变量
	        temp: 0
	      };
	    },
	
	    //初始化
	    mounted() {
	      this.$nextTick(() => {
	
	        //将从父组件中传递过来的数据赋值给中间变量
	        this.temp = this.curPage;
	
	        //修改中间变量的值
	        this.temp = 123;
	      });
	    }
	  };

#### 关于Vue中的 render: h => h(App) 具体是什么含义？
大概的翻译下：
`render: h => h(App)` 是下面内容的缩写：

	render: function (createElement) {
	    return createElement(App);
	}

进一步缩写为(ES6 语法)：

	render (createElement) {
	    return createElement(App);
	}

再进一步缩写为：

	render (h){
	    return h(App);
	}

按照 ES6 箭头函数的写法，就得到了：

	render: h => h(App);

#### 使用ES6中的属性简写

	new Vue({
	  router
	});

是下面代码的简写形式

	new Vue({
	  router: router
	});

#### Do not use built-in or reserved HTML elements as component id: select
	使用标签名select作为组件的name属性值(name: "select")时在console中产生的警告，不能将标签名设为组件的name属性

#### 代码简写
**:clone="cloneData"**表示给draggable标签的clone属性赋值为cloneData，这里是v-bind:clone="cloneData"的简写					 	  

	<draggable :clone="cloneData" :list="form_list" :options="dragOptions1"></draggable>
	
#### 正则匹配
下面代码表示匹配 **.png、.jpeg、.jpg、.gif、.svg** 类型的图片，其中代码中的 **\\.** 表示点号，因为点也是一个正则匹配符号，所以需要使用 **\\** 转义

	test: /\.(png|jpe?g|gif|svg)(\?.*)?$/
	
#### 数组中的元素改变后，触发视图更新

	this.$set(this.list, this.index, this.userDetail)
	
#### 动态添加对象属性，并触发视图更新

	this.$set(this.columnDetail, 'imageUr', '')
	
#### 重置表单

	//给表单注册引用信息
	<Form ref="userForm"></Form>
	
	//重置表单
	this.$refs['userForm'].resetFields()
	
#### 动态设置 img 标签的 src 属性，将`assetsPublicPath`属性的值由

	<img :src="require(`@/assets/images/${greenLight}`)" alt="">
	
	greenLight: "none.gif",

#### 使用相对路径的方式设置背景图片的路径

	<style lang="less" scoped>
	.exit {
	  background-image: url('~@/assets/images/exit.png');
	}
	</style>
	
其中 @ 表示配置的路径别名，表示 src 目录

	chainWebpack: config => {
		config.resolve.alias
		.set('@', resolve('src'))
    }
	
#### 使用相对路径的方式设置图片路径

	<img src="~@/assets/header_images/logo.png"/>
	
#### 自定义表单项的验证规则

	export default {
	  data() {
		const validateFile = (rule, value, callback) => {
		  if (!this.dataForm.file) {
			callback(new Error("必填项，不能为空"));
		  } else {
			callback();
		  }
		};

		return {
		  dataForm: {
			file: ""
		  },
		  
		  rules: {
			file: [
			  { required: true, validator: validateFile, trigger: "blur" },
			  { required: true, validator: validateFile, trigger: "change" }
			]
		  }
		};
	  },

	  created() {
	  },

	  mounted() {
	  },

	  methods: {
	  }
	};
	
#### 单个表单字段的验证

	this.$refs.userForm.validateField('userName', (valid) => {
      if (!valid) {
      }
    })
	
#### 清除所有表单字段的验证

使用这个方法会清空表单项的值

	this.$refs['dataForm'].resetFields()
	
#### 项目打包时提示 Error: CSS minification error: Unknown browser kaios

	删除 node_modules 文件夹 --> 删除 package-lock.json 文件 --> 执行 npm install 安装 npm 包
	
#### TypeError: token.type.endsWidth is not a function

把 vue 项目跑起来后出现 ** TypeError: token.type.endsWidth is not a function ** 报错

{% img blog-image /images/2021120201.png %}

将下面的代码



	  <img
		:src="
		  require('../../../assets/report/white_report.gif')
		"
	  >
	 
改成这种形式后可以解决这个报错

	  <img
		:src="require('../../../assets/report/white_report.gif')"
		alt=""
	  >
	  
#### vue 与 vue-template-compiler 的版本不一致

当运行项目时遇到如下错误表示 vue 与 vue-template-compiler 的版本不一致
{% img blog-image /images/2022011801.png %}

**解决方法：**

执行 npm list vue 命令查看当前项目中采用的 vue 版本，通过下图可知当前项目采用的 vue 版本是 2.6.14
{% img blog-image /images/2022011802.png %}

执行 npm list vue-template-compiler 命令查看当前项目中采用的 vue-template-compiler 版本，通过下图可知当前项目中采用的 vue-template-compiler 版本是 2.6.12
{% img blog-image /images/2022011803.png %}

通过前面两步操作可知当前项目中 vue 版本和 vue-template-compiler 的版本不一致，一般的解决方法是降低 vue 版本或升高 vue-template-compiler 的版本，由于 vue 
是安装在全局的，降低 vue 版本后担心会影响其它项目的使用，我这里采用的解决方式是升高 vue-template-compiler 的版本
首先执行 npm uninstall vue-template-compiler 命令卸载项目中已经安装的 vue-template-compiler
{% img blog-image /images/2022011804.png %}

vue-template-compiler 卸载完成之后执行 npm install vue-template-compiler@2.6.14 命令安装 2.6.14 版本的 vue-template-compiler 使 vue-template-compiler 的
版本和 vue 的版本保持一致
{% img blog-image /images/2022011805.png %}
	  
#### 页面加载完后调用的方法

	this.$nextTick(() => {
	});
	  
#### 常用 npm 命令

	安装依赖
    npm install
	
	安装指定版本号的 npm 包
	这里以安装版本号为 2.6.14 的 vue-template-compiler 为例
	npm install vue-template-compiler@2.6.14
	
	卸载 npm 包
	这里以卸载 vue-template-compiler 为例
	npm uninstall echarts
	
	执行项目
	npm run dev
	
	查看 npm 包的版本
	这里以查看 vue 的版本为例
	npm list vue 
	
	查看当前使用的 npm 镜像源
	npm get registry
	
	将 npm 镜像源设置为淘宝镜像
	npm config set registry https://registry.npmmirror.com
	
	安装 cnpm
	npm install -g cnpm --registry=https://registry.npmmirror.com
	
	
#### 参考链接
- [生成的css文件中background url()图片路径问题](https://github.com/vuejs/vue-loader/issues/481#)  
- [关于Vue中的 render: h => h(App) 具体是什么含义？](https://segmentfault.com/q/1010000007130348)
- [ECMAScript 6入门](http://es6.ruanyifeng.com/)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用Vue.js时遇到的问题及解决方法](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8Vue-js%E6%97%B6%E9%81%87%E5%88%B0%E7%9A%84%E9%97%AE%E9%A2%98%E5%8F%8A%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95/)】