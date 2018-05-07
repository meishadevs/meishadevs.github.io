---
title: SQL Server数据库学习笔记
categories:
  - 数据库
tags:
  - SQL
  - SQL Server
  - 数据库
date: 2018-05-07 20:50:54
---

年后来深圳花费了一个多月总算勉强找到了一份程序开发的工作，截止到现在已经入职块一个月了，现在还处于试用期，SQL Server数据库是公司给我安排的第二个任务，对于数据库这块我还是有点熟悉，因为我之前做的开源项目[电商网](https://github.com/meishadevs/dswz)的服务器端是使用PHP和MySQL实现的，公司要求使用SQL Server数据库，所以我花费了两天时间熟悉了一下SQL Server数据库和SQL语句，怕以后忘记所以做了一些笔记。
<!--more-->

#### 创建一个记录学生信息的表

    create table StuInfo
    (  
    	-- 学生的编号
    	-- primary key 表示将字段stuNum设置为主键
    	-- identity(1001, 1) 表示初始值为1001,以后每插入一条数据这个值自动增加1
    	StuNum int identity(1001, 1) primary key, 
    	
    	-- 学生的姓名
        Name nvarchar(10) not null,
        
        -- 学生的年龄
        Age int not null,
        
        -- 学生的性别
        Sex nvarchar(5) not null,
        
        -- 学生的语文成绩
        Chinese float not null,  
        
        -- 学生的数学成绩
        Math float not null,  
        
        -- 学生的英语成绩
        English float not null
    );  

#### 向表中插入数据

    insert into StuInfo(Name, Age, Sex, Chinese, Math, English)
    values('刘得意', 19, '男', 60, 98, 75);
    insert into StuInfo(Name, Age, Sex, Chinese, Math, English)
    values('王锐	', 20, '男', 63, 90, 96);
    insert into StuInfo(Name, Age, Sex, Chinese, Math, English)
    values('何煜中', 19, '男', 90, 73, 82);
    insert into StuInfo(Name, Age, Sex, Chinese, Math, English)
    values('王磊', 21, '男', 87, 86, 92);

#### 删除websites表中name字段值为百度, country字段值为CN的数据
    delete from websites where name='百度' and country='CN';

#### 仅删除表test内的所有内容, 保留表的定义, 不释放空间
	delete from test;

#### 删除表test, 并释放空间, 将test删除的一干二净
	drop table test;

#### 删除表test里的内容, 并释放空间, 但不删除表的定义, 表的结构还在
	truncate table test;

#### 将websites表中name字段值为菜鸟教程的alexa字段值设置为5000, country字段值设置为USA
	update websites set alexa='5000', country='USA' where name='菜鸟教程';

#### 查询StuInfo表中的数据
	select * from StuInfo;

#### 查询websites表中name字段和country字段中的数据
	select name, country from websites;

#### 查询websites表中country字段下的不同的值
	select distinct country from websites;

#### 查询websites表中country字段值为CN的值
	select * from websites where country='CN';

#### 将websites表中的数据根据alexa字段值的大小按照升序进行排序(从小到大排序)
	select * from websites order by alexa;

#### 将websites表中的数据根据alexa字段值的大小按照降序进行排序(从大到小排序)
	select * from websites order by alexa desc;

#### 查询websites表中的前3条数据
	select top 3 * from websites;

#### 查询websites表中的前50%条数据
	select top 50 precent * from websites;

#### 查询websites表中name字段值是以G开头的数据
	select * from websites where name like 'G%';

#### 查询websites表中name字段值是以K结尾的数据
	select * from websites where name like '%K';

#### 查询websites表中name字段值包含oo的数据
	select * from websites where name like '%oo%';

#### 将websites表中的id字段设置为主键，其中pkid表示主键名
	alter table websites add constraint pkid primary key(id);

#### 选择school数据库
	use school;

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[SQL-Server数据库学习笔记](http://meishadevs.com/blog/SQL-Server%E6%95%B0%E6%8D%AE%E5%BA%93%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0/)】