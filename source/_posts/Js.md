---
title: Js
date: 2017-02-27 09:19:28
categories: Js
tags: [Js, 筆記,js]
---

javascript的一些基础知识

<!-- more -->

## fetch
```
function cnt() {

	return new Promise(function(resolve, reject) {
		var url = "https://fundhdtest.eastmoney.com/ztapi/data/index";
		var content = "Hello World";
		var myHeaders = new Headers();
		myHeaders.set("Content-Length", content.length.toString());

		var myInit = {
			method: 'GET',
			headers: myHeaders,
			mode: 'cors',
			cache: 'default'
		};

		fetch(url, myInit)
			.then(function(res) {
				console.log(res.headers);
				return res.ok ? res.json() : reject(res.statusText)
			}).then(function(data) {
				resolve(data)
			}).catch(err => reject(err))
	})

}

cnt().then(data => {
	console.log(1, data)
}).catch(err => {
	console.log(2, err)
})

```

