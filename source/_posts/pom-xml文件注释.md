---
title: pom.xml文件注释
categories:
  - SpringBoot
  - java
tags:
  - SpringBoot 
  - Java
date: 2019-05-31 13:57:23
---

<!--more-->

#### 项目名称

	<name>spring</name>

#### 项目描述

	<description>These is a Spring Boot project</description>

#### 表示 src/main/java 下的目录结构

	<groupId>com.canyou</groupId>

#### 项目根目录的名称

	<artifactId>spring</artifactId>

#### 项目的版本

	<version>0.1</version>

#### 表示这是一个meaven项目

	<packaging>pom</packaging>

#### springBoot的父级依赖，表示当前项目就是springBoot项目 

	<parent>
	   <groupId>org.springframework.boot</groupId>
	   <artifactId>spring-boot-starter-parent</artifactId>
	   <version>2.1.3.RELEASE</version>
	   <relativePath/>
	</parent>

#### 管理依赖的版本

	<properties>
	   <java.version>1.8</java.version>
	</properties>

#### 项目中的模块

	<modules>
		<module>task1</module>
		<module>task2</module>
	</modules>

#### SpringBoot项目中的依赖

	<dependencies>
	
	   <!-- 测试模块，包括 JUnit、Hamcrest、Mockito -->
	   <dependency>
		  <groupId>org.springframework.boot</groupId>
		  <artifactId>spring-boot-starter-test</artifactId>
	   </dependency>

	   <!-- Web模块 -->
	   <!-- 引入 spring-boot-starter-web 模块后可以去掉 spring-boot-starter 模块 -->
	   <!-- 因为 spring-boot-starter-web 模块自动依赖了 spring-boot-starter 模块 -->
	   <dependency>
		  <groupId>org.springframework.boot</groupId>
		  <artifactId>spring-boot-starter-web</artifactId>
	   </dependency>

	   <!-- lombok -->
	   <dependency>
		  <groupId>org.projectlombok</groupId>
		  <artifactId>lombok</artifactId>
		  <optional>true</optional>
	   </dependency>
	   
	</dependencies>


> meishadevs欢迎任何形式
>
> 的转载，但请务必注明出处，尊重他人劳动成果。
> 转载请注明： 【文章转载自meishadevs：[pom.xml文件注释]()】