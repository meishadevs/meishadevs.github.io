---
title: 使用Vue.js时遇到的问题及解决方法
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

#### 参考链接
- [生成的css文件中background url()图片路径问题](https://github.com/vuejs/vue-loader/issues/481#)  
- [关于Vue中的 render: h => h(App) 具体是什么含义？](https://segmentfault.com/q/1010000007130348)
- [ECMAScript 6入门](http://es6.ruanyifeng.com/)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用Vue.js时遇到的问题及解决方法](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8Vue-js%E6%97%B6%E9%81%87%E5%88%B0%E7%9A%84%E9%97%AE%E9%A2%98%E5%8F%8A%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95/)】