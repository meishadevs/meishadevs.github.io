---
title: idea使用技巧
categories:
  - idea
tags:
  - idea
date: 2018-08-07 11:04:05
---

## 基础用法

- **idea中导入jar包：** 将光标移动到需要导入 jar 包的类上，并按 Alt + Enter


- **快速输入输出函数：** sout + Tab键 或 sout + Enter键


- **快速输入main函数：** psvm + Tab键 或 psvm + Enter键


- **快速输入for语句：** for + Tab键 或 for + Enter键


- **查看语句快速输入的方法：** Ctrl + J


- **全局搜索：** Ctrl + Shift + F


- **单步调试时进入下一步：** F8


- **结束单步调试：** F9

- 当将 On 'Update' action 属性和 On frame deactivation 属性都设置为 Update classes and resources 后，只用在debug模式下才能实现热部署

## 高级用法

###  查找文件中是否存在重复代码块

单击菜单栏上的Analyze
{% img blog-image /images/2018112805.png %}

选择下拉列表中的Locate Duplicates选项
{% img blog-image /images/2018112806.png %}

在弹出的Sepecify Code Duplication Analysis Scope对话框中确认分析的文件，确认完毕后点击OK
{% img blog-image /images/2018112807.png %}

在弹出的Code Duplication Analysis Settings对话框中选择需要分析的文件类型，一般会默认选中，然后单击OK
{% img blog-image /images/2018112808.png %}

在弹出如下所示的窗口，表示文件中存在重复代码块，其中提示 2 duplicates, Cost: 12 in XssHttpServletRequestWrapper.java，表示XssHttpServletRequestWrapper.java中有2个重复代码块，点击提示下面的子项可以定位到重复代码块在idea中的位置
{% img blog-image /images/2018112809.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[idea使用技巧](http://meishadevs.com/blog/idea%E4%BD%BF%E7%94%A8%E6%8A%80%E5%B7%A7/)】