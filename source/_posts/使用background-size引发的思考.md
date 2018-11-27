---
title: 使用background-size引发的思考
categories:
  - CSS
tags:
  - CSS
date: 2017-10-24 10:39:05
---

昨天在一个前端交流群里一个成员提出了一个非常有趣的问题`background-size: 50%`是什么意思与`background-size: 50% 50%`到底有什么区别呢，这个问题在群里引起了一番激烈的讨论，我也尝试分析一下
<!--more-->

### background-size: 50%是什么意思
查阅[W3C](http://www.w3school.com.cn/index.html)上对[background-size](http://www.w3school.com.cn/cssref/pr_background-size.asp)的介绍后可知**background-size用于设置背景图片的宽度和高度，当给background-size属性的值设为百分比时，表示以父元素的百分比来设置背景图像的宽度和高度，如果只设置一个值，则第二个值会被设置为 "auto"**，通过这段[W3C](http://www.w3school.com.cn/index.html)上的介绍可知`background-size: 50%`是`background-size: 50% auto`的简写形式

### 猜想background-size: 50% 与 background-size: 50% 50% 的区别
通过前面的介绍可知`background-size: 50%`是`background-size: 50% auto`的简写形式，我曾天真的以为`background-size: 50% auto`与`background-size: 50% 50%`表示的是一个意思都是表示背景图片的宽度为父元素宽度的50%，背景图片的高度为父元素高度的50%，通过测试发现我被打脸了，最后得出的结论是`background-size: 50% 50%`表示的是背景图片的宽度为父元素宽度的50%，背景图片的高度为父元素高度的50%没错，`background-size: 50% auto`表示背景图片的宽度为父元素宽度的50%，背景图片的高度是根据背景图片的宽度与高度的比值计算得来的

### 计算设置了background-size: 50% 50%属性后背景图片的宽度和高度
下图是为背景图片设置了`background-size: 50% 50%`后运行在浏览器上的效果，为了比较直观，我在图片上标记了一些数值，[点击此处查看代码](http://jsbin.com/lejekuj/edit?html,output)
{% img blog-image /images/pic2.png %}
通过上图可知  
父元素的宽度 = 500px  
父元素的高度 = 400px  
背景图片的宽度 = 父元素的宽度 X 50% = 500px X 50% = 250px  
背景图片的高度 = 父元素的高度 X 50% = 400px X 50% = 200px

### 计算设置了background-size: 50% 属性后背景图片的宽度和高度
下图是为背景图片设置了`background-size: 50%`后运行在浏览器上的效果，为了比较直观，我在图片上标记了一些数值，[点击此处查看代码](http://jsbin.com/nifodib/edit?html,output)
{% img blog-image /images/pic3.png %}
通过上图可知  
父元素的宽度 = 500px  
父元素的高度 = 400px  
图片文件的宽度与高度的比值 = 图片文件的宽度 / 图片文件的高度 = 128px / 96px = 1.33  
背景图片的宽度 = 父元素的宽度 X 50% = 500px X 50% = 250px  
背景图片的高度 = 背景图片的宽度 / 图片文件的宽度与高度的比值 = 250px / 1.33 =  187.97px

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用background-size引发的思考](http://meishadevs.com/blog/%E4%BD%BF%E7%94%A8background-size%E5%BC%95%E5%8F%91%E7%9A%84%E6%80%9D%E8%80%83/)】