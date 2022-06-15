---
title: blob文件下载
date: 2022-06-15 08:31:21
tags: 功能
categories: 功能
---

# blob文件下载

整体思路为，获取到后端返回的`blob`文件流后，通过`a`标签的`href`属性，载入数据流，还可以自定义文件名称。

```js
const utils = {
	downloadFile(id) {
		return http.post('/download-file', {}, {
            responseType: 'blob',
        })
    }
};

async downloadFile() {
	await utils.downloadFile(this.$route.query.id).then(res => {
       const blob = new Blob([res.data]);
       const a = document.createElement("a");
       a.download = "fileName.xlsx"; // 自定义文件名称
       a.style.disply = "none";
       a.href = URL.createObjectURL(blob);
       document.body.appendChild(a);
       a.click();
       URL.revokeObjectURL(a.href);
       document.body.removeChild(a);
   });    
};
```

> 注意
>
> 1. `responseType`必须为`blob`或者`arraybuffer`，否则下载的文件会损坏，数据无法正确展示
