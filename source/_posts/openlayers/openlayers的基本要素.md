---
title: openlayers的基本要素
date: 2022-06-25 09:36:59
tags: 
- gis
- openlayers
categories:
- openlayers
---

# openlayers的基本要素

## Map

地图的容器，每一个`gis`都需要生成一个`map`实例，所有的操作都需要在`Map`实例上进行。

```js
this.olMap = new Map({
    layers: [],
    view: new View({}),
    controls: defaults({}), // 控件
    target: this.$refs.olMap, // 容器的dom
})
```



## View

地图的窗口（即我们在电脑上能显示的内容）
