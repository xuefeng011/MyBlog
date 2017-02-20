---
title: css3新特性
date: 2017-02-20 11:18:54
categories: CSS
tags: [CSS, 筆記,CSS3]
---

CSS3 新特性

------------

<!-- more -->

###  box-shadow
  `x轴偏移量  y轴偏移量 【阴影模糊半径】 【阴影扩展班级】 【阴影颜色】 【投影方式】
                           inset outset（默认）`
###  border-image
  `repeat（重复） round（平铺） stretch（拉伸）  `

###  linear-gradient/radial-gradient

`linear-gradient(to bottom,#ff,#999)`

`渐变类型 (渐变方向，颜色起始点和结束点)`

|    角度    |    用英文    |    作用    |
| :------------: | :-------------:|: --------------------: |
|    0deg    |    to top    |    从下向上    |
|    90deg    |    to right |    从左向右    |
|    180deg    |    to bottom|    从上向下    |
|    270deg    |    to left  |    从右向左    |
|         |    to top left  |    从右下角向左上角    |
|      |    to top right |    从左下角到右上角    |


### text-overflow/word-wrap

`text-overflow:clip | ellipsis `

`clip 剪切`
`ellipsis 显示省略标记`

但是text-overflow只是用来说明文字溢出时用什么方式显示，要实现溢出时产生省略号的效果，还须定义强制文本在一行内显示（white-space:nowrap）及溢出内容为隐藏（overflow:hidden），只有这样才能实现溢出文本显示省略号的效果，代码如下：
`
text-overflow:ellipsis; 
overflow:hidden; /*溢出内容隐藏*/
white-space:nowrap;  /*强制在一行内显示*/
`

`word-wrap:normal | break-word`
`normal 控制连续文本换行`
`break-word 内容在边界内换行`

### @font-face

`
@font-face{
    font-family : 字体名字;
    src : 字体文件在服务器上的相对或者绝对路径;
}
`

###  text-shadow
`text-shadow: X-Offset Y-Offset blur color`
`X-Offset 阴影水平偏移距离 正值向右`
`Y-Offset 阴影垂直偏移距离 正值向下`
`Blur 是指阴影的模糊程度，其值不能是负值，如果值越大，阴影越模糊，反之阴影越清晰，如果不需要阴影模糊可以将Blur值设置为0；`
`Color 颜色`
`text-shadow: 0 1px 1px #fff`

### background-origin 原始起始位置
`background-origin : border-box | padding-box | content-box `
`边框 | 内边距（默认） | 内容区域`
![ss](http://img.mukewang.com/531003de0001166903660166.jpg)

### background-clip 背景图剪切
`background-clip : border-box | padding-box | content-box | no-clip`
`边框（默认） | 内填充 | 内容区域 `

### background-size 背景图大小
`background-size : auto | <长度值> | <百分比> | cover | contain `
>* auto 默认值
* <长度值> 宽度  等比缩放
* <百分比> 0~100% 
* cover **覆盖** 填满整个容器
* contain **容纳** 紧贴容器边缘

### multiple backgrounds 多重背景
`
    background-image: url(http://img.mukewang.com/54cf2365000140e600740095.jpg),
                      url(http://img.mukewang.com/54cf238a0001728d00740095.jpg),
                      url(http://img.mukewang.com/54cf23b60001fd9700740096.jpg);
    background-position: left top, 100px 0, 200px 0;
    background-repeat: no-repeat, no-repeat, no-repeat;
`

### 导航菜单
`
	/*使用伪元素制作导航列表项分隔线*/
	.nav li:after{
		    content:'|';
		    margin-left:10px;
		    color:#fff;
		}
`
`
	.nav li{
		   background:linear-gradient(to left,#000,#000,#000) no-repeat right/1px 15px }
		}
`
`
.nav li:after{
          content:"";
          position:absolute;
          right:0px;
          top:16px;
          height:19px;
          width:1px;    
    	  background:linear-gradient(to top,red, orange,yellow,green,blue,indigo,violet)   
        }
`


### 属性选择器
>|属性选择器|描述|
|:---------------------:|:-----------------------------------------:|
|E[att^="val"]| 以val开头 |
|E[att$="val"]| 以val结尾 |
|E[att*="val"]| 以val包含|

### 结构性伪类选择器--root
`根选择器  匹配元素所在文档的根元素 也就是<html>`