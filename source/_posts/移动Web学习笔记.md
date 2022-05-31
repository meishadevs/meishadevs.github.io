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
**解释：**语种名称代码，这个代码表示网页中使用的是英语[点击此处查看详细解释](http://www.ruanyifeng.com/blog/2008/02/codes_for_language_names.html)  

**5. rel="apple-touch-icon"**  
**解释：**在iPhone, iPad上的safari浏览器中有个将网站添加到主屏幕上的按钮，当网站设置了**rel="apple-touch-icon**属性，当网站添加到屏幕上，屏幕上会显示网站的图标[点击此处查看详细解释](http://blog.sina.com.cn/s/blog_5a073f0f01014jfc.html)

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

**12. em**  
**解释：** em为相对长度单位。相对于当前对象内文本的字体尺寸  
当em作为font-size的单位时，表示相对于父元素的font-size的倍数  
例如：父元素的font-size的值为 16px  
如果子元素的font-size: 2em，则子元素的字体大小为 16px X 2em = 32px  
当em作为其他属性单位时，代表自身字体大小的倍数  
例如：一个元素的font-size: 16px  
如果该元素的line-height: 2em，则该元素的行高为 16px X 2em = 32px  

**13. rem**  
**解释：**rem是CSS3新引进的一个度量单位，其数值表示根节点(html标签)的字体大小的倍数，在当前的所有主流浏览器中根节点(html标签)的字体大小都为16px，即 html标签的font-size:16px，1rem = 16px,为了让后面方便计算，通常将1rem的值设为10px，通过将html标签的font-size值设为62.5%可以将html标签的font-size值设置为10px，因为 16px X 62.5% = 10px，此时以后凡是html标签下的标签都可以使用rem，例如在html标签下有个p标签，要将p标签的高度设为50px可以写成`p {height: 5rem;}`[点击此处查看详细介绍](http://www.w3cplus.com/css3/define-font-size-with-css3-rem)

**14. -webkit-font-smoothing: antialiased**  
**解释：**`-webkit-font-smoothing`属性用于定义字体的平滑属性。有关字体平滑的介绍可参考[字体渲染](http://ued.ctrip.com/blog/font-rendering.html)一文，目前该属性已从W3C标准中移除，慎用！  
其属性值`antialiased`表示使用灰阶平滑

**15. 自定义滚动条的样式**  
**::-webkit-scrollbar** 滚动条整体部分  
**::-webkit-scrollbar-thumb**  滚动条里面的小方块，能向上向下移动（或往左往右移动，取决于是垂直滚动条还是水平滚动条）  
**::-webkit-scrollbar-track** 滚动条的轨道（里面装有Thumb）  
**::-webkit-scrollbar-button** 滚动条的轨道的两端按钮，允许通过点击微调小方块的位置。  
**::-webkit-scrollbar-track-piece** 内层轨道，滚动条中间部分（除去）  
**::-webkit-scrollbar-corner** 边角，即两个滚动条的交汇处  
**::-webkit-resizer** 两个滚动条的交汇处上用于通过拖动调整元素大小的小控件

**15.** `<meta name="apple-touch-fullscreen" content="yes">`  
**解释：**添加到主屏幕上后全屏显示  

**16.** `<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=no">`  
**解释：** 所有运行在移动端浏览器中的网页都必须添加这个标签，其中name='viewport'表示视口、width=device-width表示网页的宽度等于浏览器窗口的宽度、initial-scale=1.0表示网页的初始化缩放比例其中1.0表示不缩放、maximum-scale=1.0表示网页的最大缩放比例、minimum-scale=1.0表示网页的最小缩放比例、user-scalable=no表示不允许用户自己缩放网页

**17.** `<meta name="format-detection" content="telephone=no">`  
**解释：**告诉浏览器不要将页面中的数字识别为电话号码

**18.** `<meta name="google-site-verification" content="">`  
**解释：**将网站添加进google网站管理，有利于google的收录

**19.** `<meta name="screen-orientation"   content="portrait">`  
**解释：**浏览器使用竖屏显示网页

**20.** `<meta name="screen-orient" content="landscape">`  
**解释：**浏览器使用横屏显示网页

**21.** `<meta name="apple-mobile-web-app-capable" content="yes">`  
**解释：**启用webapp的全屏模式，删除iPad或者iPhone上默认的工具栏和菜单栏

**22.** `<meta name="full-screen" content="yes">`  
**解释：**在UC浏览器中强制使用全屏显示网页

**23.** `<meta name="x5-fullscreen" content="true">`  
**解释：**在QQ浏览器中强制使用全屏显示网页

**24.** `spellcheck="false"`  
**解释：**给类似于textarea、input标签添加`spellcheck="false"s属性后当向标签中输入的单词拼写错误，不会产生红色的波浪线

**25.** `-webkit-appearance: none`  
**解释：**`-webkit-appearance`用于改变按钮和其他控件的外观，使其类似于原生控件，其属性值`none`用于去除系统默认appearance的样式，常用于IOS下移除原生样式

**26.** `<input type="search">`  
***解释：**使用`<input type="search">`制作搜索框，当在手机上点击搜索框时会弹出一个软键盘，软键盘上的enter按钮会以搜索按钮的形式显示 

**27.** `<meta http-equiv="X-UA-Compatible" content="ie=edge">`  
**解释：**如果网页在IE浏览器上运行，使用最新的edge浏览器渲染网页

**28.** `<meta http-equiv="Cache-Control" content="no-cache">`  
**解释：**Cache-Control表示指定请求和响应遵循的缓存机制，其中no-cache表示不缓存请求的消息或者响应的消息[点击此处查看详细介绍](http://blog.csdn.net/m0_38073829/article/details/75453050)

**29.** `<meta http-equiv="cache-control" content="no-store">`  
**解释：**Cache-Control表示指定请求和响应遵循的缓存机制，其中no-store用于防止重要的信息被无意的发布[点击此处查看详细介绍](http://blog.csdn.net/m0_38073829/article/details/75453050)

**30.** `<meta http-equiv="Pragma" content="no-cache">`  
**解释：**Pragme用于定义页面缓存，其中no-cache表示不缓存页面[点击此处查看详细介绍](http://blog.csdn.net/m0_38073829/article/details/75453050)

**31.** `<link rel="dns-prefetch" href="">`  
**解释：**预解析技术，当你浏览网页时，浏览器会在加载网页时对网页中的域名进行解析缓存，这样在你单击当前网页中的连接时就无需进行DNS的解析，减少用户等待时间，提高用户体验，[点击此处查看详细介绍](http://www.sojson.com/blog/218.html)

**32.** `<meta name="apple-mobile-web-app-status-bar-style" content="black">`  
**解释：**iphone的私有标签，它用于给iphone上的safari浏览器顶端的状态栏设置样式

**33.** `<meta content="email=no" name="format-detection" />`  
**解释：**告诉浏览器不要识别页面上的邮箱地址

**34.** `<meta name="imagemode" content="force"/>`  
**解释：**强制显示标签

**35.** `<meta name="theme-color" content="#BF3030">`  
**解释：**使用浏览器访问网页时，改变浏览器上状态栏的背景颜色

**36.** `<meta name="HandheldFriendly" content="true"> `  
**解释：**使得手持设备能正常的渲染移动端页面，使得不识别 viewport 的浏览器能正常渲染移动端页面，比如：黑莓  

**37.** `<meta name="MobileOptimized" content="320"> `  
**解释：**使得微软的老式浏览器能渲染移动端能正常的渲染移动端页面  

**38.** `<meta http-equiv="cleartype" content="on">`  
**解释：**不使用clearType字体

## 参考链接
- [CSS3自定义滚动条样式 -webkit-scrollbar](https://www.xuanfengge.com/css3-webkit-scrollbar.html)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[移动Web学习笔记](http://meishadevs.com/blog/移动Web学习笔记)】