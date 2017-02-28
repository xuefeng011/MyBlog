---
title: js判断APP是否安装
date: 2017-02-28 10:28:03
categories: JS
tags: [JS, 筆記,js判断APP是否安装]
---

js判断移动端是否安装某款app的方法

<!-- more -->



```
	< script language="javascript">
 if (navigator.userAgent.match(/(iPhone|iPod|iPad);?/i)) {
  var loadDateTime = new Date();
  window.setTimeout(function() {
   var timeOutDateTime = new Date();
   if (timeOutDateTime - loadDateTime < 5000) {
    window.location = "要跳转的页面URL";
   } else {
    window.close();
   }
  },
  25);
  window.location = " apps custom url schemes ";
 } else if (navigator.userAgent.match(/android/i)) {
  var state = null;
  try {
   state = window.open("apps custom url schemes ", '_blank');
  } catch(e) {}
  if (state) {
   window.close();
  } else {
   window.location = "要跳转的页面URL";
  }
 }
  <  /script>

```

apps custom url schemes 是什么呢？

其实就是你与APP约定的一个协议URL，你的IOS同事或Android同事在写程序的时候会设置一个URL Scheme， 例如设置： URL Scheme ：app 然后其他的程序就可以通过URLString ＝ app:// 调用该应用。 还可以传参数，如：

app://reaction/?uid=1

原理：500ms内，本机有应用程序能解析这个协议并打开程序，调用该应用；如果本机没有应用程序能解析该协议或者500ms内没有打开这个程序，则执行setTimeout里面的function，就是跳转到你想跳转的页面。 


