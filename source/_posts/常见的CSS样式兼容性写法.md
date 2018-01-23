---
title: 常见的CSS样式兼容性写法
date: 2017-03-05
categories:
	- CSS
tags:
    - CSS
---

自己平时整理的一些CSS样式的兼容性写法
<!--more-->

##### 1. 设置透明度

	在IE6中使用 filter: alpha(opacity = 40);
	在其他浏览器中使用 opacity: 0.4;

##### 2. 设置行高

	/*\9表示兼容所有的IE浏览器*/  
	line-height: 35px\9;

##### 3. 清除浮动

	 .clearfix:after {
	    content: '';
	    height: 0;
	    clear: both;
	    overflow: hidden;
	    visibility: hidden;
	    display: block;
	}

	.clearfix {
	    *zoom: 1;
	}

##### 4. 禁止用户选择文本
	
	 -moz-user-select: -moz-none;
    -khtml-user-select: none;
    -webkit-user-select: none;
    -ms-user-select: none;
    user-select: none;

##### 5. 使用flex布局

	display: -webkit-box;
    display: -webkit-flex;
    display: flex;

##### 6. 使用绝对定位将子元素元素的宽度设为父元素宽度的100%，将子元素的高度设为父元素高度的100%

	.parent {
		position: relative
	}

	.child {
		 position: absolute;
	     left: 0;
	     right: 0;
	     top: 0;
		 bottom: 0;
	}

##### 7. 使用绝对定位加CSS3中的transform将子元素设置到父元素的正中间

	.parent {
        position: relative;
    }

	.child {
		-webkit-transform: translate(-50%, -50%);
    	-moz-transform: translate(-50%, -50%);
	    -ms-transform: translate(-50%, -50%);
	    -o-transform: translate(-50%, -50%);
	    transform: translate(-50%, -50%);
	    position: absolute;
	    left: 50%;
	    top: 50%;
	}

##### 8. 隐藏溢出标签中的文本并且在标签最后增加一个省略号

	overflow: hidden;
	white-space: nowrap;
	text-overflow: ellipsis;

##### 9. 使子元素相对于父元素在水平方向和竖直方向上都居中

	.parent {
        position: relative;
    }

    .child {
        margin: auto;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
    }

##### 10. 在移动设备上设置 1px 大小的边框

 	.border-1px {
        position: relative;
    }

    .border-1px::after {
        content: '';
        width: 100%;
        border-top: 1px solid #ccc;
        display: block;
        position: absolute;
        left: 0;
        bottom: 0;
    }

    /* 如果网页在最小屏幕像素比为1.5的移动设备上运行 */
    @media (-webkit-min-device-pixel-ratio: 1.5),(min-device-pixel-ratio: 1.5) {
        .border-1px::after {
            -webkit-transform: scaleY(0.7);
            transform: scaleY(0.7);
        }
    }

    /* 如果网页在最小屏幕像素比为2的移动设备上运行 */
    @media (-webkit-min-device-pixel-ratio: 2),(min-device-pixel-ratio: 2) {
        .border-1px::after {
            -webkit-transform: scaleY(0.5);
            transform: scaleY(0.5);
        }
    }

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[http://meishadevs.com/blog/一些常见的CSS兼容性写法](http://meishadevs.com/blog/%E4%B8%80%E4%BA%9B%E5%B8%B8%E8%A7%81%E7%9A%84CSS%E5%85%BC%E5%AE%B9%E6%80%A7%E5%86%99%E6%B3%95/)】