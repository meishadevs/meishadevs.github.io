---
title: GoJS爬坑之旅
categories:
  - GoJS
tags:
  - GoJS
date: 2018-07-05 21:00:39
---
我进入项目组后参加了第一次项目会议，在会议上项目经理为每个项目成员都分配了任务，我的任务是使用GoJS实现一个拖拽效果，这也是我第一次听说GoJS，在网上查阅相关的资源后发现GoJS的资料比较少，而且绝大多数资源都是英文的，这也为我学习及使用这个框架带来了不小的困难，好在项目经理看出这块做起来比较难后来又加了一个人，现在这块由我和一个同事两个人共同开发。
<!--more-->

# GoJS是什么
通过查看[GoJS官网](https://gojs.net/latest/index.html)可知**GoJS**是一款基于JavaScript的图表绘制组件，使用**GoJS**可以绘制流程图、UML图、家族关系图、树形图等。

# 使用GoJS绘制的一些图形

## 使用GoJS绘制流程图
下图是使用GoJS绘制的一个流程图，这也是官方提供的示例中的一个，也可以访问[https://gojs.net/latest/samples/flowchart.html](https://gojs.net/latest/samples/flowchart.html)查看流程图效果，同时还可以访问[https://gojs.net/latest/samples/index.html](https://gojs.net/latest/samples/index.html)查看GoJS官方提供的所有示例
![](http://oq3pg8pg4.bkt.clouddn.com/2018070601.jpg)

## 使用GoJS绘制一个简单的图表

### 引入GoJS文件
根据[GoJS官网](https://gojs.net/latest/doc/download.html)上的介绍可知，引入GoJS的方式有三种，分别是：下载GoJS文件将GoJS文件放在项目中使用并在项目中引用、通过CDN引入GoJS、通过npm包引入GoJS，这里我们使用最简单的方式，使用第一种方式，根据[GoJS下载页](https://gojs.net/latest/doc/download.html)中的提示下载go.js文件，[GoJS下载页](https://gojs.net/latest/doc/download.html)中提示用户可以选中下载go-debug.js文件或下载go.js文件,其中go-debug.js用于开发环境，因为使用go-debug.js时会在控制台中打印一些调试信息便于调试，go.js文件用户生产环境，这里我们直接下载go.js文件，下载好后创建一个HTML文件直接引入就可以了
![](http://oq3pg8pg4.bkt.clouddn.com/2018070602.png)

### 编写实现代码
下面是一段简单的GoJS代码

	<!doctype html>
	<html lang="en">
	<head>
	    <meta charset="UTF-8">
	    <title>GoJS绘制的一个简单的图表</title>
	    <script src="./go.js"></script>
	    <script>
	        function init() {
	
	            //表示在id为"myDiagramDiv"的标签上绘制GoJS图表
	  var diagram = new go.Diagram("myDiagramDiv");
	
	            diagram.model = new go.GraphLinksModel(
	                [
	                    //绘制一个节点，节点的key值为"Hello"，其中GoJS中的key值不会重复，是GoJs中的标识
	  { key: "Hello" },
	
	                    //绘制一个节点，节点的key值为"World!"，GoJS中的key值不会重复，是GoJs中的标识
	  { key: "World!" }
	                ],
	                [
	                    //在key值为"Hello"的节点与key值为"World!"的节点之间绘制一条连线
	  { from: "Hello", to: "World!" }
	                ]
	            );
	        }
	    </script>
	</head>
	<body onload="init()">
	    <div id="myDiagramDiv" style="border: solid 1px blue; width:400px; height:150px"></div>
	</body>
	</html>

执行结果，因为GoJS是收费的，可以免费使用，但是不支付授权费在左上角会有一个水印，并且有些功能不能使用
![](http://oqdvwkahb.bkt.clouddn.com/2018070603.png)

#### 破解GoJS 
除了支付授权费还可以通过破解的方式去除左上角的水印，破解方式是使用打开go.js文件或者go-debug.js文件并注释掉go.js文件或者go-debug.js中的下面这段代码

	b[w.Kg("7ca11abfd022028846")]=w.Kg("398c3597c01238");for(var c=["5da73c80a36755dc038e4972187c3cae51fd22","32ab5ff3b26f42dc0ed90f22432913b54ae6247590da4bb21c324ba3a84e385776","54a702f3e53909c447824c6706603faf4cfb236cdfda5de14c134ba1a95a2d4c7cc6f93c1387","74bf19bce72555874c86"],d=1;5>d;d++)b[w.Kg("7ca11abfd7330390")](w.Kg(c[d-1]),10,15*d+0);b[w.Kg("7ca11abfd022028846")]=w.Kg("39f046ebb36e4b");for(d=1;5>d;d++)b[w.Kg("7ca11abfd7330390")](w.Kg(c[d-
	1]),10,15*d+0);if(4!==c.length||"5"!==c[0][0]||"7"!==c[3][0])w.p=function(a,b){var c=new da(a,b,2);Object.freeze(c);a[b]=c;var d=a.fv;d instanceof ma||(d=new ma("string",da),a.fv=d);d.add(b,c);return c};

破解成功后可以看到图表上已经没有水印
![](http://oqdvwkahb.bkt.clouddn.com/2018070604.png)

## 使用GoJS实现一个拖拽效果

下图是我使用GoJS实现的一个简单的拖拽效果，整个拖拽界面由两部分组成，左侧菜单和右侧画布，左侧菜单中包含容器、计算、存储、容灾、CDM节点，用户根据需要将节点拖入对应容器中，例如：计算节点只能拖入计算容器中，存储节点只能拖入存储容器中等，当将节点拖入与节点不匹配的容器中时，节点不能添加到容器中，当将节点添加到对应的容器中后会给节点编号，例如第一个计算节点命名为计算1，第二个计算节点命名为计算2，当删除节点时会对容器中已有的节点重新编号
![](http://oqdyj5870.bkt.clouddn.com/20180802.png)
项目地址：[http://meishadevs.com/JavaScriptDemo/拖拽效果/](http://meishadevs.com/JavaScriptDemo/%E6%8B%96%E6%8B%BD%E6%95%88%E6%9E%9C/)  
项目源码：[https://github.com/meishadevs/JavaScriptDemo/tree/master/拖拽效果](https://github.com/meishadevs/JavaScriptDemo/tree/master/%E6%8B%96%E6%8B%BD%E6%95%88%E6%9E%9C)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/GoJS爬坑之旅/](http://meishadevs.com/blog/GoJS%E7%88%AC%E5%9D%91%E4%B9%8B%E6%97%85/)】