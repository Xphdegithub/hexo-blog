---
title: typora使用图床
date: 2022-05-04 21:44:10
tags: typora
---
# 在`typora`中使用图床

## 图床是什么？

图床是在互联网中存储图片的空间，其实就是云存储图片🐶

## 为什么要使用图床？

1. 减轻服务器的压力

2. 便于文件的迁移

   举个例子🌰

   ![image-20220504220205797](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504220205797.png)

   这个狗狗🐕在我的电脑是可以正常显示的，但是当我换一台电脑呢？显而易见，肯定是加载不出来的。

   这就有了图床的用武之地，如果我们用图床，这个问题就会迎刃而解。（如下图）

   ![image-20220504220606770](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504220606770.png)

## 图床的获取

目前国内有很多图床，如`smms`、`腾讯云COS`、`GitHub图床`、`七牛图床`、`阿里云图床`等。有收费的，也有免费的。

我使用了`腾讯云COS`,它免费赠送了`50G`的空间，马哥这点还是挺良心的，嘿嘿。

以下为腾讯云的例子

![image-20220504221315971](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504221315971.png)

![image-20220504221508711](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504221508711.png)

![image-20220504221532851](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504221532851.png)

![image-20220504221737782](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504221737782.png)

![image-20220504221823359](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504221823359.png)

![image-20220504221843163](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504221843163.png)

## 在typroa中使用图床

1. 首先我们要下载`Picgo`，并对其进行配置

![image-20220504222436647](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504222436647.png)

> - 版本需要为v5
>
> - `SecretId`和`SecretKey`可以在`https://console.cloud.tencent.com/cam/capi`查看（第一次进入是没有的，可以自行创建）。

要想上传成功，`PicGo`的端口必须和`Typora`的一致

![image-20220504222743593](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504222743593.png)

2. 配置`Typora`

   ![image-20220504223256805](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504223256805.png)

出现以下情况即为上传成功~

![image-20220504223329966](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220504223329966.png)

在`Typora`插入图片后，右键 ---> 上传图片  --->  链接自动替换为图床路径

造就完了，兄弟~