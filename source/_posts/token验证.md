---
title: token验证
categories:
  - Node.js
tags:
  - Node.js
date: 2022-12-12 16:19:49
---

本篇文章是介绍 [store-node](https://github.com/meishadevs/store-node) 项目中 token 验证的方式，store-node 是基于 node.js、express、mongodb、mongoose 开发的的[电商网项目](https://github.com/meishadevs/store-vue)服务端
<!--more-->

## 启动项目

根据[项目文档](https://github.com/meishadevs/store-node/blob/master/README.md)中的介绍搭建好项目环境，并且运行项目，当 Vscode 下的 控制台中显示如下所示的信息时，表示项目运行成功
{% img blog-image /images/2022121201.png %}

## 验证接口
在[接口文档](https://github.com/meishadevs/store-node/blob/master/API.md)任意选择一个接口放在 postman 中调用，当接口有响应值时，表示项目成功的运行起来了，接口能正常访问
{% img blog-image /images/2022121202.png %}

## 获取 token
当访问某些需要验证 token 的接口时在没有配置 token，或配置的 token 无效时，会返回一个 “accessToken无效” 的提示信息，表示这个接口需要配置 token 才能访问
{% img blog-image /images/2022121203.png %}

调用[登录接口](https://github.com/meishadevs/store-node/blob/master/API.md#%E7%99%BB%E5%BD%95)，并填写正确的用户名和密码后，调用成功后会返回最新的 token
{% img blog-image /images/2022121204.png %}

## 配置 token
有了 token 后我们就可以在 Postman 中配置 token，首先打开 Postman，选择请求方式，填写需要使用 Postman 发起请求的 api 接口
{% img blog-image /images/2022121205.png %}

选择 Postman 上的 Headers 选项卡
{% img blog-image /images/2022121206.png %}

在 KEY 中填写 Authorization
{% img blog-image /images/2022121207.png %}

在 VALUE 中填写在前面步骤中获取的 token，填写格式是 Bearer + token，Bearer 和 token 之间需要有一个空格
{% img blog-image /images/2022121208.png %}

## 发送请求

点击发送按钮，接口中有返回值后表示接口调用成功，也表示 token 验证成功
{% img blog-image /images/2022121209.png %}

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[token验证](http://meishadevs.com/blog/token验证/)】