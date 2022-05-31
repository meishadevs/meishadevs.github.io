---
title: 使用echarts绘制地图
categories:
  - echarts
tags:
  - echarts
date: 2021-09-09 10:12:49
---

最近我参与了几个数据大屏可视化项目，项目中要求在大屏上以地图的形式直观的展示某一地区的某个业务数据，在绘制地图时踩的坑还是挺多的，特此用一篇博客记录一下绘制地图的过程，下面会以展示江西省下面各城市手机品牌数为例介绍地图的绘制方法。
<!--more-->

#### 获取地理数据

绘制地图时需要用于展示地图的地理数据，地理数据是一个 geoJSON 格式的数据，本质上是一个 json 数据

打开 [地图选择器](http://datav.aliyun.com/tools/atlas/index.html)
{% img blog-image /images/2021090901.png %}

在地图上选择江西省所在的区域
{% img blog-image /images/2021090902.png %}

单击鼠标左键，此时会进入江西省区域下
{% img blog-image /images/2021090903.png %}

在右边的属性面板中点击其它类型中的下载按钮
{% img blog-image /images/2021090904.png %}

此时会将江西省的地理数据以一个 json 数据的形式下载到本地
{% img blog-image /images/2021090905.png %}

创建一个前端项目，在项目目录下放入 echarts 核心库文件和下载下来的江西省地理数据 json 文件和 jquery 文件，读完 json 数据时会用到 jquery 
{% img blog-image /images/2021090906.png %}

#### 项目代码

	<!DOCTYPE html>
	<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>地图</title>
		<style>
			.container {
				width: 1000px;
				margin: 0 auto;
			}
	
			.container .title {
				font-size: 28px;
				font-weight: 300;
				font-family: 'Microsoft YaHei';
				text-align: center;
			}
		
			.container .main {
				height: 900px;
			}
		</style>
		<script src="./jquery.min.js"></script>
		<script src="./echarts.min.js"></script>
	</head>
	
	<body>
		<div class="container">
			<div class="title">手机品牌分布地图</div>
			<div class="main"></div>
		</div>
		<script>
	
			// 获得地理数据的 url
			var dataUrl = "./jiangxi.json";
		
			var mapData = [
				{
					name: '南昌市',
					value: [115.892151, 28.676493]
				},
				{
					name: '景德镇市',
					value: [117.214664, 29.29256]
				},
				{
					name: '萍乡市',
					value: [113.852186, 27.622946]
				},
				{
					name: '九江市',
					value: [115.80, 29.5]
				},
				{
					name: '新余市',
					value: [114.90, 27.90]
				},
				{
					name: '鹰潭市',
					value: [117.033838, 28.238638]
				},
				{
					name: '赣州市',
					value: [114.940278, 25.85097]
				},
				{
					name: '吉安市',
					value: [114.986373, 27.111699]
				},
				{
					name: '宜春市',
					value: [115, 28.5]
				},
				{
					name: '抚州市',
					value: [116.358351, 27.7]
				},
				{
					name: '上饶市',
					value: [117.8, 28.7]
				}
			];
		
			// 手机列表
			var cellPhoneList = [
				{
					name: '南昌市',
					apple: 10,
					samsung: 20,
					xiaomi: 30,
					huawei: 40
				},
				{
					name: '景德镇市',
					apple: 40,
					samsung: 30,
					xiaomi: 20,
					huawei: 10
				},
				{
					name: '萍乡市',
					apple: 40,
					samsung: 10,
					xiaomi: 20,
					huawei: 30
				},
				{
					name: '九江市',
					apple: 40,
					samsung: 10,
					xiaomi: 30,
					huawei: 20
				},
				{
					name: '新余市',
					apple: 40,
					samsung: 20,
					xiaomi: 10,
					huawei: 30
				},
				{
					name: '鹰潭市',
					apple: 40,
					samsung: 20,
					xiaomi: 30,
					huawei: 10
				},
				{
					name: '赣州市',
					apple: 10,
					samsung: 30,
					xiaomi: 20,
					huawei: 40
				},
				{
					name: '吉安市',
					apple: 10,
					samsung: 40,
					xiaomi: 30,
					huawei: 20
				},
				{
					name: '宜春市',
					apple: 30,
					samsung: 20,
					xiaomi: 10,
					huawei: 40
				},
				{
					name: '抚州市',
					apple: 30,
					samsung: 40,
					xiaomi: 20,
					huawei: 10
				},
				{
					name: '上饶市',
					apple: 30,
					samsung: 10,
					xiaomi: 20,
					huawei: 40
				}
			];
		
			var myChart = echarts.init(document.querySelector('.main'));
		
			var appleDom = '<span style="width:10px;height:10px;margin-right:5px;background-color:#fff94f;border-radius:50%;display:inline-block;"></span>'
			var samsungDom = '<span style="width:10px;height:10px;margin-right:5px;background-color:#2b8bf3;border-radius:50%;display:inline-block;"></span>'
			var xiaomiDom = '<span style="width:10px;height:10px;margin-right:5px;background-color:#3dd477;border-radius:50%;display:inline-block;"></span>'
			var huaweiDom = '<span style="width:10px;height:10px;margin-right:5px;background-color:#f00;border-radius:50%;display:inline-block;"></span>'
		
			$.get(dataUrl, (json) => {
				// 注册地图
				echarts.registerMap('jx', json);
		
				var option = {
					// 标题
					title: {
						show: false
					},
		
					tooltip: {
						trigger: 'item'
					},


				// 地理坐标系组件
					geo: {
						map: 'jx',
						zoom: 1.2,
		
						label: {
							show: false
						},
		
						itemStyle: {
							areaColor: 'rgba(4,73,128, 1)',
		
							// 设置外层边框
							borderWidth: 2,
							borderColor: 'rgba(34,216,255, 1)',
							shadowColor: 'rgba(34,216,255, 1)', // #044B4D
							shadowOffsetY: 7,
							shadowOffsetX: 7,
							shadowBlur: 6
						}
					},
		
					series: [
						{
							// 图表的类型为散点图（地图上的黄色旗子）
							type: 'scatter',
							name: 'hasProperty',
		
							// 采用的坐标系为地理坐标系
							coordinateSystem: 'geo',
		
							// 散点图上点的大小（旗子的大小）
							symbolSize: 20,
		
							// 标记的图形
							symbol: function (value, params) {
								return 'image://data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABYAAAAWCAYAAADEtGw7AAABh0lEQVQ4jdXVvWtVQRDG4SdREIJgEwuJBi3URlBEiYUWKgSDhVgrFhb5BwIWipWNvRDETkhQAmlSplACQRKIjQoWIgh+FBokGj8IiiOLc8MlnJv7wW18YWDZd+a35+zZMytCKzEZISIMtpivV3saxdZWKlpKqtMNnMc4nuNXWj/wAV86BRcdwb0G3ju8xbN2t6KZduMEHnQbXHQfc90Gr2CsDLoN3oEDnYDnm/g9uFO47YIv4TIWsIzVipxjuNrJcZvMqFI/9mOgE/BmWs7o+sdb1/8H3rjHgziX/WAfRhrUncK1bERLmMW3qq24mGf0De7iZI4b6TN+4wqm8REP84H+KcLtbOJ/IoxH2FvRuBs1+p4IQxEepb8W4ULxirmSky83uRGa3SD96ZeYqYFv1k1ORDhcUXgmwmiE7Rvmt0QYjvAk639GGCleeZWis7iO0/m/v8dTvM5x/a+7E7twEMez8axhCrfwqiTVwDUN5CJHcQh7EtSHbfie19CnXPQFFvEYX9cp+As8wAD9SbJQaQAAAABJRU5ErkJggg=='
							},
		
							// 区名称的样式
							label: {
								show: true,
								formatter: '{b}',
								position: 'bottom',
								color: '#fff',
								fontSize: 14
							},
		
							itemStyle: {
								color: '#ddb926'
							},
		
							tooltip: {
								show: false
							},
		
							data: this.mapData
						},
						{
							// 图表类型为地图
							type: 'map',
		
							// 使用 registerMap 注册的地图名称
							mapType: 'jx',
		
							// 地图缩放比例
							zoom: 1.2,
		
							// 提示框
							tooltip: {
								triggerOn: 'mousemove',
								backgroundColor: 'rgba(8, 8, 8, .85)',
								textStyle: {
									color: '#fff',
									fontSize: 16
								},
		
								// 处理悬浮提示
								formatter: (params) => {
									return (
										params.data.name + '<br/>' +
										appleDom + '苹果：' + params.data.apple + '<br/>' +
										huaweiDom + '华为：' + params.data.huawei + '<br/>' +
										xiaomiDom + '小米：' + params.data.xiaomi + '<br/>' +
										samsungDom + '三星：' + params.data.samsung + '<br/>'
									)
								}
							},
		
							// 标签的样式
							label: {
		
								// 标签在默认状态下的样式
								normal: {
									show: false
								},
		
								// 标签在高亮状态下的样式
								emphasis: {
									show: false
								}
							},
		
							// 选中状态下的样式
							select: {
								// 标签在选中状态下的样式
								label: {
									show: false
								},
		
								// 选中状态下地图上区域块的样式
								itemStyle: {
									areaColor: '#2b8bf3'
								}
							},
		
							// 地图上区域块的样式
							itemStyle: {
								// 默认状态下地图的颜色
								normal: {
									areaColor: '#083288',
									borderColor: 'rgba(0, 210, 255, 1)', // #00d2ff
									borderWidth: 2,
									color: '#fff'
								},
		
								// 选中状态下地图的颜色
								emphasis: {
									areaColor: '#2b8bf3',
								}
							},
		
							data: cellPhoneList
						}
					]
				};
		
				myChart.setOption(option);
			});
		</script>
	</body>
	</html>

#### 执行结果
{% img blog-image /images/2021090907.png %}

#### 效果演示
**[查看效果](https://meishadevs.github.io/JavaScriptDemo/%E5%9C%B0%E5%9B%BE/)**

#### 全部代码
**[查看全部代码](https://github.com/meishadevs/JavaScriptDemo/tree/master/%E5%9C%B0%E5%9B%BE)**


#### 参考链接
- [地图选择器](http://datav.aliyun.com/tools/atlas/index.html)

> meishadevs欢迎任何形式的转载，但请务必注明出处，尊重他人劳动成果。
转载请注明： 【文章转载自meishadevs：[使用echarts绘制地图](https://meishadevs.com/blog/使用echarts绘制地图)】