---
title: MongoDB数据库学习笔记
categories:
  - MongoDB
  - 数据库
tags:
  - MongoDB
  - 数据库
date: 2022-09-27 13:40:07
---

#### 查看 MongoDB 数据库的版本

	db.version();
	
#### 查看 MongoDB 下的所有数据库

	show dbs
	
#### 进入某个数据库下

	use dbname
	
#### 查看数据库下的所有集合

	show collections
	
#### 创建集合
	
	# name 为集合名称
	db.createCollection(name)
	
#### 重命名集合

	# sourceName 原集合名称
	# newName 新集合名称
	db.sourceName.renameCollection("newName")
	
#### 数据备份

	# -h 数据库地址
	# -d 数据库名称
	# -o 数据文件的路径
	mongodump -h 192.168.10.178:27017 -d store -o F:\database
	
#### 数据还原
	
	# -h 数据库地址
	# -d 数据库名称，数据文件的路径
	mongorestore -h 192.168.10.178:27017 -d store F:\database
	
#### 不能通过 ip 访问数据库的解决方法
修改 bin 目录下 mongod.cfg 文件，将 bindIp 属性值改成 0.0.0.0
{% img blog-image /images/2022101701.png %}
	
#### 参考资料
- [MongoDB教程](http://c.biancheng.net/mongodb2/)
- [Mongoose 实现关联查询和踩坑记录](https://cloud.tencent.com/developer/article/1683003?from=article.detail.1445359)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[MongoDB数据库学习笔记](http://meishadevs.com/blog/MongoDB数据库学习笔记)】