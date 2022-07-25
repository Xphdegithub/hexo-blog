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

- ####  `display: grid; / display: inline-grid;`

  这是`Grid`布局的开端，在设置这个属性后，这个元素也就成为了`Grid`布局的**容器**，其下的直系元素会成为**项目**。

- #### `grid-template-colums`和`grid-template-rows`

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

- #### `repeat()`

  用于简化重复的值。该函数有2个参数，第一个为重复的次数，第二个为重复的值。

```css
.wraper { 
	//...
    grid-template-rows: repeat(2, 50px); // 等同于 grid-template-rows: 50px 50px;
}
```

- #### `auto-fill`关键字

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

- #### `fr`关键字

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

- #### `minmax()`

产生一个长度范围，表示长度就在这个范围中，都可以应用到网格项目中。它接受2个参数，分别为最小值和最大值。

```css
.wraper {
    display: grid;
    // 表示创建3列，最后一列的宽最小为300px，最大为600px
    grid-template-columns: 200px 300px minmax(300px, 600px);
    grid-auto-rows: 50px;
    grid-row-gap: 5px;
    grid-column-gap: 5px;
}
```

![grid-minmax](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/grid-minmax-16583934632933.gif)

- #### `auto`关键字

由浏览器决定长度

```css
.wraper {
    display: grid;
    // 表示创建3列，中间的那一列自适应宽度
    grid-template-columns: 200px auto 200px;
    grid-auto-rows: 50px;
    grid-row-gap: 5px;
    grid-column-gap: 5px;
}
```

![grid-auto](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/grid-auto.gif)

- #### `row-gap、column-gap、gap`

前两个属性分别设置行的间距和列的间距，最后一个属性是前两个的简写形式

```css
.wraper {
    display: grid;
    grid-template-columns: 200px 200px 200px;
    grid-auto-rows: 50px;
    row-gap: 5px;
    column-gap: 5px;
    // 等同于 gap: 5px;
}
```

![image-20220721172452860](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220721172452860.png)

> 注：在`row-gap、column-gap、gap`前加`grid-`也是可以的（如：`grid-row-gap`），但是这种写法已废弃，不建议使用。

- #### `grid-template-areas`和`grid-area`（项目属性）

`grid-template-areas`用于定义区域，一个区域由一个或多个单元格组成

`grid-area`用于指定**项目**放在哪个区域

```css
.wraper {
    display: grid;
    grid-template-columns: 200px 200px 200px;
    // 自定义区域名称
    grid-template-areas: 
        "one two three"
        "four five six";
    grid-auto-rows: 50px;
    row-gap: 5px;
    column-gap: 5px;
}
.wraper div:nth-of-type(1) {
    background: #5fc7af;
    // 指定名称来控制所处区域
    grid-area: six;
}
.wraper div:nth-of-type(2) {
    background: #9ac5b7;
    grid-area: five;
}
.wraper div:nth-of-type(3) {
    background: #ceba7d;
    grid-area: four;
}
.wraper div:nth-of-type(4) {
    background: #96bcdd;
    grid-area: three;
}
.wraper div:nth-of-type(5) {
    background: #e3cfaf;
    grid-area: two;
}
.wraper div:nth-of-type(6) {
    background: #e4b0a1;
    grid-area: one;
}
```

![image-20220725084455163](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220725084455163.png)

若不想用到某个区域或定义空的单元格，使用`.`即可

```css
.wraper {
    display: grid;
    grid-template-columns: 200px 200px 200px;
    // 自定义区域名称
    grid-template-areas: 
        ". two three"
        "four five six";
    grid-auto-rows: 50px;
    row-gap: 5px;
    column-gap: 5px;
}
```

```html
// 使用到的区域数量需要和grid-template-area中的非空单元格对应，不然空的单元格也会显示出来
<main class="wraper">
    <div>1</div>
    <div>2</div>
    <div>3</div>
    <div>4</div>
    <div>5</div>
</main>
```

![image-20220725084913213](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220725084913213.png)

- #### `grid-auto-flow`

`grid-auto-flow: row | column | dense | row dense | column dense;`

用于控制自动布局算法的运作方式，精确指定在网格中被自动布局的元素的排列方式。默认的排列方式是“先行后列”，即先填满一行，再开始第二行。`grid-auto-flow`的默认值为`row`

> 注意：
>
> 1. `grid-auto-flow: row`对应的是`grid-template-columns`（只有一行有多列的时候才能按先行后列【先横着排】）
> 2. `grid-auto-flow: column`对应的是`grid-template-rows`（只有存在多行的时候才能先列后行【先竖着排】）

```css
.wraper {
    display: grid;
    grid-template-columns: 100px 200px 100px;
    grid-auto-flow: row;
    row-gap: 5px;
    column-gap: 5px;
    grid-auto-rows: 50px;
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
    grid-column: 1 / 2 span;
}
.wraper div:nth-of-type(7) {
    background: #ceeacc;
}
.wraper div:nth-of-type(8) {
    background: #d47273;
}
.wraper div:nth-of-type(9) {
    background: #beeae2;
}
```

![image-20220725101113159](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220725101113159.png)

当**项目**元素的大小不一致的时候会出现以上这种情况，这是因为第六个元素的大小太大了，不足以在第二行占满一行，被挤了下来，但是在实际开发过程中，我们不需要这个空白部分。这个时候，我们可以设置`grid-auto-flow: row dense;`，表示尽可能的填满表格，但是顺序会被打乱。

![image-20220725101524586](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220725101524586.png)
