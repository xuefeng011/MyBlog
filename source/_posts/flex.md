---
title: flex
date: 2017-02-22 09:52:15
categories: CSS
tags: [css,笔记,flex]
---

## Flex 布局整理

<!-- more -->


* 布局的传统解决方案，基于盒状模型，依赖 display属性 + position属性 + float属性。它对于那些特殊布局非常不方便，比如，垂直居中就不容易实现。

* 兼容性
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071003.jpg)

* 注意，设为Flex布局以后，子元素的`float`、`clear`和`vertical-align`属性将失效。


![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071004.png)
*容器默认存在两根轴：水平的主轴（`main axis`）和垂直的交叉轴（`cross axis`）。主轴的开始位置（与边框的交叉点）叫做`main start`，结束位置叫做`main end`；交叉轴的开始位置叫做`cross start`，结束位置叫做`cross end`。
项目默认沿主轴排列。单个项目占据的主轴空间叫做`main size`，占据的交叉轴空间叫做`cross size`。

### flex-direction属性
```
.row{
	flex-direction:row | row-reverse | column | column-reverse;
}

```
* row（默认值）：主轴为水平方向，起点在左端。
* row-reverse：主轴为水平方向，起点在右端。
* column：主轴为垂直方向，起点在上沿。
* column-reverse：主轴为垂直方向，起点在下沿。

### flex-wrap 属性
```
.box{
	flex-wrap : nowrap | wrap | wrap-reverse;
}

```

* nowrap（默认）：不换行。
* wrap: 换行，第一行在上方
* wrap-reverse : 换行，第一行在下方

### flex-flow 属性
```
.box{
	flex-flow:row nowrap;
}

```

### justify-content 属性
* 属性定义了项目在主轴上的对齐方式。
```
.box{
	justify-content: flex-start | flex-end | center | space-between | space-around;
}
```
* flex-start（默认值）：左对齐
* flex-end：右对齐
* center： 居中
* space-between：两端对齐，项目之间的间隔都相等。
* space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071010.png)

### align-item 属性
* 定义项目在交叉轴上如何对齐

```
.box{
	align-item: flex-start | flex-end | center | baseline | stretch;
}
```
* flex-start：交叉轴的起点对齐。
* flex-end：交叉轴的终点对齐。
* center：交叉轴的中点对齐。
* baseline: 项目的第一行文字的基线对齐。
* stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。

![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071011.png)

### align-content 属性
* 定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
```
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}

```
* flex-start：与交叉轴的起点对齐。
* flex-end：与交叉轴的终点对齐。
* center：与交叉轴的中点对齐。
* space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
* space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
* stretch（默认值）：轴线占满整个交叉轴。



## 项目的属性

### order 属性
* 定义项目的排列顺序。数值越小，排列越靠前，默认为0。
```
.item {
  order: <integer>;
}
```
### flex-grow 属性
* 属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
```

.item {
  flex-grow: <number>; /* default 0 */
}

```

### flex-shrink 属性
* 定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
```
item {
  flex-shrink: <number>; /* default 1 */
}

```

### flex-basis 属性
* 定义了在分配多余空间之前，项目占据的主轴空间（`main size`）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小。
* 它可以设为跟`width`或`height`属性一样的值（比如`350px`），则项目将占据固定空间。
```
.item {
  flex-basis: <length> | auto; /* default auto */
}
```

### flex 属性
* 是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选。
* 该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
```
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}

```

### align-self 属性
* 允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`。
```
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}

```
![](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071016.png)






