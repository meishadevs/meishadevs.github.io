---
title: 移动Web学习笔记
categories:
  - 移动Web
tags:
  - 移动Web
date: 2017-08-31 10:23:03
---

整理的一些移动Web相关的知识点
<!--more-->

**1. -webkit-text-size-adjust: 100%**  
**解释：**在 Chrome 浏览器中只能设置大于或等于 12px 的字体大小，当设置了小于 12px 的字体大小时，浏览器按照 12px 的字体大小渲染字体，而设置了 **-webkit-text-size-adjust** 属性后浏览器可以渲染 12px 以下的字体大小

**2. -webkit-tap-highlight-color: transparent**  
**解释：**这个属性只用于iOS (iPhone和iPad)。当你点击一个链接或者通过Javascript定义的可点击元素的时候，它就会出现一个半透明的灰色背景，设置 **-webkit-tap-highlight-color: transparent**时就不会产生这个背景

**3. lang="zh-cmn-Hans"**  
**解释：**语种名称代码，这个代码表示网页中使用的是简体普通话，详细介绍可以参考[http://www.ruanyifeng.com/blog/2008/02/codes_for_language_names.html](http://www.ruanyifeng.com/blog/2008/02/codes_for_language_names.html)

**4. lang="en"**  
**解释：**语种代码，这个代码表示网页中使用的是英语  

**5. rel="apple-touch-icon"**  
**解释：**用于设置Apple iPhone, iPad上的网页图标，当将使用了rel="apple-touch-icon"属性的网站添加到iPhone或者iPad上的收藏夹里的时候，收藏夹上会显示这个图标，当没有设置rel="apple-touch-icon"属性的时候，收藏夹上显示整张网页的截图

**6. 在IOS上实现模糊效果的代码**

	-webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);

**7. 禁止单击鼠标左键并移动鼠标时拖拽图片方法二**
	
	<img src="bg1.png" draggable="false">
	<img src="bg2.png" draggable="false">

**8.** `<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">`  
**解释：** 所有运行在移动端浏览器中的网页都必须添加这个标签，其中name='viewport'表示视口、width=device-width表示网页的宽度等于浏览器窗口的宽度、initial-scale=1.0表示网页的初始化缩放比例其中1.0表示不缩放、maximum-scale=1.0表示网页的最大缩放比例、minimum-scale=1.0表示网页的最小缩放比例、user-scalable=no表示不允许用户自己缩放

**9.** `<meta name="format-detection" content="telephone=no">`  
**解释：**表示HTML代码中的电话号码不应显示为超文本链接

**10.** `<meta name="google-site-verification" content="">`  
**解释：**将自己网站添加进google网站管理，有利于google的收录

**11.** `<meta name="screen-orientation" content="portrait">`  
**解释：**网页在UC浏览器上强制使用竖屏显示

**12.** `<meta name="apple-mobile-web-app-capable" content="yes">`  
**解释：**是否启用 WebApp 全屏模式，删除苹果默认的工具栏和菜单栏

**13.** `<meta name="full-screen" content="yes">`  
**解释：**在UC浏览器中强制使用全屏展示网页

**13.** `<meta name="x5-fullscreen" content="true">`
**解释：**在QQ浏览器中强制使用全屏显示网页

**14.** `spellcheck="false"`  
**解释：**给类似于textarea、input标签添加`spellcheck="false"s属性后当向标签中输入的单词拼写错误，不会产生红色的波浪线

**15.** `-webkit-appearance: none`  
**解释：**清除浏览器的默认样式  

**16.** `<input type="search">`  
***解释：**使用`<input type="search">`制作搜索框，当在手机上点击搜索框时会弹出一个软键盘，软键盘上的enter按钮会以搜索按钮的形式显示 

**17.** `<meta http-equiv="X-UA-Compatible" content="ie=edge">`  
**解释：**如果网页在IE浏览器上运行，使用最新的edge浏览器渲染网页

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/移动Web学习笔记/](http://meishadevs.com/blog/移动Web学习笔记/)】