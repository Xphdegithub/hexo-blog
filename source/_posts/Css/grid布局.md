---
title: Grid布局
date: 2022-07-19 11:22:32
tags: css
categories: css
---

# Grid布局

我原本以为`flex`已经天下无敌了，没想到有布局比它还勇猛，这是谁的部将……😂

<div>
    <img src="https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220719112426804.png" />
</div>

## Grid布局是什么？

`Grid`布局即网格布局，是一种新的`css`布局模型，它比`flex`布局还要强大，是一种二维布局。目前貌似在`pc`端的兼容性可能不太好（其实也还可以，可能就IE不是很好吧，具体看公司的业务需求吧），但是在移动端应该是完全魔门忒的😁，还是很值得学习的。

## Grid布局的概念即使用

在`Grid`布局中，属性可分为两类，一类为**容器属性**，一类为**项目属性**。

### 容器属性

- `display: grid; / display: inline-grid;`

  这是`Grid`布局的开端，在设置这个属性后，这个元素也就成为了`Grid`布局的**容器**，其下的直系元素会成为**项目**。

- `grid-template-colums`和`grid-template-rows`

  这两个属性分别定义了网格中的列和行，构成了`grid`布局中的二维系统

```html
<main class="wraper">
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
    <div>6</div>
</main>
```

```css
.wraper {
    display: grid;
    grid-template-columns: 200px 100px 200px; // 声明列宽分别为200px 100px 200px的3列
    grid-template-rows: 50px 50px; // 声明行高都为50px的2行
    
}
.wraper div {
    color: #fff;
}
.wraper div:nth-of-type(1) {
    background: #5fc7af;
}
.wraper div:nth-of-type(2) {
    background: #9ac5b7;
}
.wraper div:nth-of-type(3) {
    background: #ceba7d;
}
.wraper div:nth-of-type(4) {
    background: #96bcdd;
}
.wraper div:nth-of-type(5) {
    background: #e3cfaf;
}
.wraper div:nth-of-type(6) {
    background: #e4b0a1;
}
```

![image-20220720094819077](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220720094819077.png)

- `repeat()`

  用于简化重复的值。该函数有2个参数，第一个为重复的次数，第二个为重复的值。

```css
.wraper { 
	//...
    grid-template-rows: repeat(2, 50px); // 等同于 grid-template-rows: 50px 50px;
}
```

- `auto-fill`关键字

表示自动填充，让一行（或一列）中尽可能的容纳更多的单元格。

```css
.wraper {
    display: grid;
    // 表示列宽200px，但列的数量是不固定的，只要浏览器能够容纳得下，就可以放置元素
    grid-template-columns: repeat(auto-fill, 200px); 
    grid-auto-rows: 50px;
    grid-row-gap: 5px;
    grid-column-gap: 5px;
}
```

![ezgif.com-gif-maker](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/ezgif.com-gif-maker.gif)

- `fr`关键字

`grid`布局还引入了一个另外的长度单位来帮助我们创建灵活的网格轨道。`fr`单位代表网格容器中的一等份。

```css
.wraper {
    display: grid;
    // 表示创建3列，第一列的宽度固定为200px，后面两列分别占剩余宽度的 2 / 3 和 1 / 3
    grid-template-columns: 200px 2fr 1fr;
    grid-auto-rows: 50px;
    grid-row-gap: 5px;
    grid-column-gap: 5px;
}
```

![grid-fr](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/grid-fr.gif)
