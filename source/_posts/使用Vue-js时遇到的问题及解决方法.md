---
title: 使用Vue.js时遇到的问题及解决方法
categories:
  - Vue.js
tags:
  - Vue.js

date: 2017-12-01 16:14:29
---

**1.在执行 npm run dev 命令的时候出现8080端口被占用**  
在任务管理器中手动结束所有Node.exe进程
<!-- more -->

**2.使用v-for指令遍历组件时产生警告，提示需要在组件上增加一个key属性**  
在组件上添加一个key属性

	<router-link to="/select" v-for="content in item.classContent" :key="content.id">{{ content }}</router-link>

**3.[Vue warn]: Do not use built-in or reserved HTML elements as component id: head**  
不能使用标签名作为组件名

**4.执行npm run build命令构建Vue.js项目后，在浏览器中打开生成的HTML文件，网站资源文件的路径错误**  
进入项目目录下的`config/index.js`文件中的`build`对象下的`assetsPublicPath`属性，将`assetsPublicPath`属性的值由 `assetsPublicPath: '/'`，改成 `assetsPublicPath: './'`

**5.执行npm run build命令构建Vue项目后，生成的CSS文件中background url()图片路径错误**  
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

**6. vue.esm.js?f077:574 [Vue warn]: Avoid mutating a prop directly since the value will be overwritten whenever the parent component re-renders. Instead, use a data or computed property based on the prop's value. Prop being mutated: "selectIndex"**  
不能修改`  props: ['selectIndex']`中的`selectIndex`

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用Vue.js时遇到的问题及解决方法](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8Vue-js%E6%97%B6%E9%81%87%E5%88%B0%E7%9A%84%E9%97%AE%E9%A2%98%E5%8F%8A%E8%A7%A3%E5%86%B3%E6%96%B9%E6%B3%95/)】