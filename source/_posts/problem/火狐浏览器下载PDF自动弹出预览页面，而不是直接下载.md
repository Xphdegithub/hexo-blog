---
title: 火狐浏览器下载PDF自动弹出预览页面，而不是直接下载
date: 2022-07-13 15:50:03
tags:
 - 火狐
 - problem
categories:
 - problem
---

# 火狐浏览器下载PDF自动弹出预览页面，而不是直接下载

问题描述: 将`html`转换为`pdf`后，使用`a`标签的`download`进行下载，这在谷歌浏览器下没有任何问题，流畅的雅痞，但是在**火狐**浏览器下却会直接弹出预览的页面，在这个页面点击下载才能下载文件，并且下载的文件名丢失了，变为了`document.pdf`……😤

## 解决方案

经过一番查阅资料和向大佬询问后得知：出现这样的情况可能是火狐未遵循`a`标签的`download`规范，并且弹出预览页面为浏览器的自动行为，并不能通过代码直接控制。

虽然我们不能通过代码直接控制浏览器的行为，但是我们可以通过修改文件的类型为不可预览的类型，曲线救国😄，这样火狐浏览器就不会弹出预览页面了

以下为核心代码：

```js
 let link = document.createElement("a");
 let body = document.querySelector("body");

 link.href = window.URL.createObjectURL(
 	new Blob([blob], {
        type: "text/html;chartset=UTF-8",
      })
    );
link.download = pdfName + ".pdf";
link.target = "_blank";
link.style.display = "none";
body.appendChild(link);
link.click();
body.removeChild(link);
window.URL.revokeObjectURL(link.href);
```

> 1. 当我们获取到`pdf`的二进制文件（`blob`）后，给他设置为不可预览的文件类型，然后进行后续操作即可……美汁汁儿😂
>
> 2. 此处有个注意的地方，我们需要手动给文件设置后缀，如此处的`.pdf`，否则可能会导致文件无法打开
