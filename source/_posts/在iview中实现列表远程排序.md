---
title: 在iview中实现列表远程排序
categories:
  - Vue
  - iview
tags:
  - Vue
  - iview
date: 2019-04-23 20:56:06
---

iview中可以通过给列表中每个字段设置sortable: true可以实现字段排序，但是当列表中的数据量比较多时，列表中会有分页，此时只能对当前页进行排序，针对这个问题,iview中有一个远程排序功能，可以通过远程排序实现多页数据的排序
<!--more-->

**第一步：** 在Table中监听触发排序的事件
{% img blog-image /images/2019022302.png %}

**第二步：**将需要排序的字段的sortable属性的值改成custom
{% img blog-image /images/2019022303.png %}

**第三步：**在数据查询对象中增加用于字段排序的属性，其中filed表示要排序的字段，sortType表示排序的类型
{% img blog-image /images/2019022304.png %}

**第四步：**每触发一次字段排序，都调用一次获得列表的方法，并将当前排序的字段名和排序方式通过api传递给后台

	 // 对客户信息排序
	sortCustomer(column, key, order) {
	  // 排序的字段
	  this.listQuery.filed = column.key

	  // 排序的方式
	  this.listQuery.sortType = column.order
	  this.getCustomerList()
	}

**第五步：**在实体类中增加filed字段何sortType字段

	 /**
	 * 根据filed字段排序
	 */
	@TableField(exist = false)
	private String filed;


	/**
	 * 排序的类型
	 */
	@TableField(exist = false)
	private String sortType;

**第六步：** 在mapper中根据传递过来的参数实现相应的排序

	 <if test="filed == 'fullName' and sortType == 'desc'">
		order by customer.full_name desc
	</if>
	<if test="filed == 'fullName' and sortType == 'asc'">
		order by customer.full_name asc
	</if>
	<if test="filed == 'idType' and sortType == 'desc'">
		order by customer.id_type desc
	</if>
	<if test="filed == 'idType' and sortType == 'asc'">
		order by customer.id_type asc
	</if>
	<if test="filed == 'orderPerson' and sortType == 'desc'">
		order by wxUser.wechat_name desc
	</if>
	<if test="filed == 'orderPerson' and sortType == 'asc'">
		order by wxUser.wechat_name asc
	</if>
	<if test="filed == 'orderDate' and sortType == 'desc'">
		order by tempOrder.orderDate desc
	</if>
	<if test="filed == 'orderDate' and sortType == 'asc'">
		order by tempOrder.orderDate asc
	</if>

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[在iview中实现列表远程排序](http://meishadevs.com/blog/在iview中实现列表远程排序/)】