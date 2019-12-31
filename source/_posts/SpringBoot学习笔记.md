---
title: SpringBoot学习笔记
categories:
  - Java
  - SpringBoot
tags:
  - Java
  - SpringBoot
date: 2019-05-31 14:16:06
---

<!--more-->

##### 只要有一次更新失败，就会出现回滚

	@Transactional(rollbackFor = {Exception.class})


##### 在实体类中局部配置字段策略

	@ApiModelProperty(value = "出生日期")
	@TableField(value = "birthday", updateStrategy = FieldStrategy.IGNORED)
	private LocalDate birthday;

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[SpringBoot学习笔记]()】