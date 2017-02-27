---
title: box model
date: 2017-02-22 13:35:22
categories: HTML
tags: [html,"笔记",box-model]
---


DIV+CSS 盒子模型

<!-- more -->


![](http://image79.360doc.com/DownloadImg/2014/10/1001/45984178_1.jpeg)
W3C标准盒子模型
包括 `margin | border | padding | content ` 并且 `content` 部分不包含其他部分


![](http://image79.360doc.com/DownloadImg/2014/10/1001/45984178_2.jpeg)
IE 盒子模型
包括 ` margin | border | padding | content ` 和标准W3C盒子模型不通是: IE盒子模型的`content` 部分包含了`border` 和`padding`
IE模型更像是 box-sizing : border-box; 其内容宽度还包含了border和padding


## box-sizing 属性
`box-sizing : content-box|border-box|inherit;`
* (1) `content-box` ,默认值，可以使设置的宽度和高度值应用到元素的内容框。盒子的width只包含内容。
	即总宽度=`margin+border+padding+width`

* (2) `border-box` , 设置的`width`值其实是除`margin`外的`border`+`padding`+`element`的总宽度。盒子的`width`包含`border`+`padding`+内容
	即总宽度=`margin`+`width`很多CSS框架，都会对盒子模型的计算方法进行简化。

* (3) `inherit` , 规定应从父元素继承 `box-sizing` 属性的值
关于border-box的使用：

* 1 一个box宽度为100%，又想要两边有内间距，这时候用就比较好
* 2 全局设置 border-box 很好，首先它符合直觉，其次它可以省去一次又一次的加加减减，它还有一个关键作用——让有边框的盒子正常使用百分比宽度



# 一些小问题

###  margin越界
当父元素没有边框border时，设置第一个子元素的margin-top值的时候，会出现margin-top值加在父元素上的现象，解决方法有四个：
* （1）给父元素加边框border （副作用）
* （2）给父元素设置padding值  （副作用）
* （3）父元素添加 overflow：hidden （副作用）
* （4）父元素加前置内容生成。（推荐）
```
<div class="parent">
    <div class="child"></div> 
</div>
.parent {
     width : 500px;
     height : 500px;
     background-color : red;       
}
.parent : before {
     content : " ";
     display : table;
}

.child {
     width : 200px;
     height : 200px;
     background-color : green;
     margin-top : 50px;
}

```


### 浮动
* ####浮动元素与绝对定位元素的差别####
* 绝对定位的元素脱离了文档流，而浮动元素依旧在文档流中
* 同处于文档流中的文字实体不会与浮动元素重叠，而会与绝对定位元素重叠


### line-height [link](http://www.zhangxinxu.com/wordpress/2009/11/css%E8%A1%8C%E9%AB%98line-height%E7%9A%84%E4%B8%80%E4%BA%9B%E6%B7%B1%E5%85%A5%E7%90%86%E8%A7%A3%E5%8F%8A%E5%BA%94%E7%94%A8/)