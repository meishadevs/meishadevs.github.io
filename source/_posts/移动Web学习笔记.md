---
title: 移动Web学习笔记
categories:
  - 移动Web
tags:
  - 移动Web
date: 2017-08-31 10:23:03
---

**1. -webkit-text-size-adjust: 100%**  
**解释：**在 Chrome 浏览器中只能设置大于或等于 12px 的字体大小，当设置了小于 12px 的字体大小时，浏览器按照 12px 的字体大小渲染字体，而设置了 **-webkit-text-size-adjust** 属性后浏览器可以渲染 12px 以下的字体大小

<!--more-->

**2. -webkit-tap-highlight-color: transparent**  
**解释：**这个属性只用于iOS (iPhone和iPad)。当你点击一个链接或者通过Javascript定义的可点击元素的时候，它就会出现一个半透明的灰色背景，设置 **-webkit-tap-highlight-color: transparent**时就不会产生这个背景

**3. lang="zh-cmn-Hans"**  
**解释：**语种名称代码，这个代码表示网页中使用的是简体普通话[点击此处查看详细解释](http://www.ruanyifeng.com/blog/2008/02/codes_for_language_names.html)

**4. lang="en"**  
**解释：**语种代码，这个代码表示网页中使用的是英语  

**5. rel="apple-touch-icon"**  
**解释：**用于设置iPhone, iPad上的网页图标，当你将使用了rel="apple-touch-icon"属性的网页添加到iPhone或者iPad上的浏览器的收藏夹里的时候，收藏夹上会显示这个图标，当没有设置rel="apple-touch-icon"属性的时候，收藏夹上显示整张网页的截图

**6. 在iOS上实现模糊效果的代码**

	-webkit-backdrop-filter: blur(10px);
    backdrop-filter: blur(10px);

**7. 禁止单击鼠标左键并移动鼠标时拖拽图片**
	
	<img src="bg1.png" draggable="false">
	<img src="bg2.png" draggable="false">

**8. touch-callout: none**  
**解释：**当你触摸并按住触摸目标时候，禁止显示系统默认菜单

**9. -webkit-overflow-scrolling: touch**  
**解释：**-webkit-overflow-scrolling属性用于控制元素在移动设备上是否使用滚动回弹效果，其中touch表示使用具有回弹效果的滚动, 当手指从触摸屏上移开，内容会继续保持一段时间的滚动效果。继续滚动的速度和持续的时间和滚动手势的强烈程度成正比

**10. pointer-events: none**  
**解释：**当鼠标点击设置了pointer-events: none属性的标签时，标签不起作用，会出现类似于标签的禁用效果[点击此处查看详细解释](http://www.zhangxinxu.com/wordpress/2011/12/css3-pointer-events-none-javascript/)

**11. -webkit-box-sizing:border-box**  
**解释：**当你指定了一个块级元素时，并且为其定义了边框，设置了其宽度为100％。在移动设备开发过程中我们通常会对文本框定义为宽度100％，将其定义为块级元素以实现全屏自适应的样式，但此时你会发现，该元素的边框(左右)各1个像素会溢了文档，导致出现横向滚动条，为解决这一问题，我们可以为其添加一个特殊的样式`-webkit-box-sizing:border-box;`用来指定该盒子的大小包括边框的宽度

**12.** `<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">`  
**解释：** 所有运行在移动端浏览器中的网页都必须添加这个标签，其中name='viewport'表示视口、width=device-width表示网页的宽度等于浏览器窗口的宽度、initial-scale=1.0表示网页的初始化缩放比例其中1.0表示不缩放、maximum-scale=1.0表示网页的最大缩放比例、minimum-scale=1.0表示网页的最小缩放比例、user-scalable=no表示不允许用户自己缩放

**13.** `<meta name="format-detection" content="telephone=no">`  
**解释：**告诉设备不要将页面中的数字识别为电话号码

**14.** `<meta name="google-site-verification" content="">`  
**解释：**将自己网站添加进google网站管理，有利于google的收录

**15.** `<meta name="screen-orientation" content="portrait">`  
**解释：**网页在UC浏览器上强制使用竖屏显示

**16.** `<meta name="apple-mobile-web-app-capable" content="yes">`  
**解释：**启用webapp的全屏模式，删除iPad或者iPhone上默认的工具栏和菜单栏

**17.** `<meta name="full-screen" content="yes">`  
**解释：**在UC浏览器中强制使用全屏展示网页

**18.** `<meta name="x5-fullscreen" content="true">`  
**解释：**在QQ浏览器中强制使用全屏显示网页

**19.** `spellcheck="false"`  
**解释：**给类似于textarea、input标签添加`spellcheck="false"s属性后当向标签中输入的单词拼写错误，不会产生红色的波浪线

**20.** `-webkit-appearance: none`  
**解释：**清除浏览器的默认样式  

**21.** `<input type="search">`  
***解释：**使用`<input type="search">`制作搜索框，当在手机上点击搜索框时会弹出一个软键盘，软键盘上的enter按钮会以搜索按钮的形式显示 

**22.** `<meta http-equiv="X-UA-Compatible" content="ie=edge">`  
**解释：**如果网页在IE浏览器上运行，使用最新的edge浏览器渲染网页

**23.** `<meta http-equiv="Cache-Control" content="no-cache">`  
**解释：**Cache-Control表示指定请求和响应遵循的缓存机制，其中no-cache表示不缓存请求的消息或者响应的消息[点击此处查看详细介绍](http://blog.csdn.net/m0_38073829/article/details/75453050)

**24.** `<meta http-equiv="cache-control" content="no-store">`  
**解释：**Cache-Control表示指定请求和响应遵循的缓存机制，其中no-store用于防止重要的信息被无意的发布[点击此处查看详细介绍](http://blog.csdn.net/m0_38073829/article/details/75453050)

**25.** `<meta http-equiv="Pragma" content="no-cache">`  
**解释：**Pragme用于定义页面缓存，其中no-cache表示不缓存页面[点击此处查看详细介绍](http://blog.csdn.net/m0_38073829/article/details/75453050)

**26.** `<link rel="dns-prefetch" href="">`  
**解释：**预解析技术，当你浏览网页时，浏览器会在加载网页时对网页中的域名进行解析缓存，这样在你单击当前网页中的连接时就无需进行DNS的解析，减少用户等待时间，提高用户体验，[点击此处查看详细介绍](http://www.sojson.com/blog/218.html)

**27.** `<meta content="black" name="apple-mobile-web-app-status-bar-style">`  
**解释：**iphone的私有标签，它用于给iphone上的safari浏览器顶端的状态栏设置样式

**28.** `<meta content="email=no" name="format-detection" />`  
**解释：**告诉设备不要识别页面上的邮箱地址

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/移动Web学习笔记/](http://meishadevs.com/blog/移动Web学习笔记/)】