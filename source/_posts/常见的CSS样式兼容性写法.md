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

##### 5. 使用绝对定位将子元素元素的宽度设为父元素宽度的100%，将子元素的高度设为父元素高度的100%

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

##### 6. 使用绝对定位加CSS3中的transform将子元素设置到父元素的正中间

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

##### 7. 使用flex将子元素设置到父元素的正中间

	.parent {
		display: flex;
	    justify-content: center;
	    align-items: center;
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

##### 11. 使用 flex 布局的兼容性写法

	.flex {
	    display: -webkit-box;
	    display: -webkit-flex;
	    display: flex;
	}

##### 12. 使用 flex 布局实现元素均等分配

	.flex-1 {
		-webkit-flex: 1;
	    flex: 1;
	}

##### 13. /deep/ 深度选择器
当引入第三方组件后，使用深度选择器可以局部修改第三方组件的样式，避免全局样式污染

	<style lang="less" scoped>
	 /deep/ .ivu-poptip,
	 /deep/ .ivu-poptip-rel {
	   width: 100% !important;
	}
	</style>
	
在 scss 中使用 ::v-deep

	<style lang="scss" scoped>
	 ::v-deep .ivu-poptip,
	 ::v-deep .ivu-poptip-rel {
	   width: 100% !important;
	}
	</style>

##### 14. 响应式布局中屏幕尺寸的表示
这里是以 iView 框架为例，不同框架的尺寸值可能不一样

- **xs** 超小屏幕 手机 (<576px)
- **sm** 小屏幕 平板 (≥576px)
- **md** 中等屏幕 桌面显示器 (≥768px)
- **lg** 大屏幕 大桌面显示器 (≥992px)
- **xl** 超大屏幕 (≥1200px)
- **xxl** 超级大屏幕 (≥1600px)


> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[常见的CSS样式兼容性写法](http://meishadevs.com/blog/%E5%B8%B8%E8%A7%81%E7%9A%84CSS%E6%A0%B7%E5%BC%8F%E5%85%BC%E5%AE%B9%E6%80%A7%E5%86%99%E6%B3%95/)】