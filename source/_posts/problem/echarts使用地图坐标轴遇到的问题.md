---
title: echarts使用地图坐标轴遇到的问题
date: 2022-06-01 18:44:38
tags:
 - echarts
 - problem
categories:
 - problem
 - echarts
---


# 使用地图坐标轴遇到的问题

近日，需要使用`echarts`做一个地图并渲染数据的场景，效果图如下，但是由于对`echarts`的使用并不是很熟练，所以特此记录一下过程中遇到的问题，以便日后参考~

![image-20220601184948474](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220601184948474.png)

首先是地图资源的获取[阿里DataV](http://datav.aliyun.com/portal/school/atlas/area_selector#&lat=29.67402915372495&lng=121.56761992209837&zoom=8.5)，选择你想要的地图区域后下载即可，这里我下载的是`json`文件

![image-20220601190336405](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220601190336405.png)

## 问题1：地图的注册

`echarts`给出的接口是`echarts.registerMap('name', mapsSource)`进行注册

我们需要使用接口请求本地或服务器来引入地图资源，这里我使用`axios`来请求本地资源进行导入，但是接口返回一直是404，经过一番搜索后发现，问题出现在地图资源的存放上，我将地图资源放到了`src/assets/maps/`下（具体为啥在了解后补充），应该放在`public`目录下，再后来又发现一种导入方式，就是直接`import`将地图资源导入，然后直接当参数传入即可使用

```
import mapSource from '@/assets/maps/chongqing.json';

this.$echarts.registerMap("chongqing", mapSource);
```

## 问题2：坐标的转换

地图中类似雷达扫描的元素是一个加了动画的`div`，但是这个元素的位置需要根据接口返回的经纬度数据来决定（好尴尬😅，不知道咋弄……），经过一番百度，发现`echarts`提供了这个接口（更尴尬了……）。

![image-20220601192920051](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220601192920051.png)

这个接口返回的是一个数组`[经度, 纬度]`

## 问题3：整个地图区域设置渐变色

最终效果如下图

![image-20220615090706568](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220615090706568.png)

`echarts`虽然提供了设置区域为渐变色的配置项（`itemStyle.areaColor`），但是设置的是单个区域的渐变，这会使得整个地图的每个区域都是分开的渐变，如下图

![image-20220615091047043](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220615091047043.png)

经过一番查阅，得到了解决问题的灵感，既然`itemStyle.areaColor`设置的是单个区域的颜色，那么地图不要子区域不就行了，但是业务要求还需要子区域的选择，所以我们只要将`geo`的每个子区域的颜色设置为透明，这样就只有地图的边界线了，然后再设置`series.type[map]`为一个没有子区域的完成地图，再给其设置相应的渐变，这样就达成了我们的目的。perfect……😘
