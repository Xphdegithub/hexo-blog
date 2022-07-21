---
title: 清除text-indent对img的影响
date: 2022-06-14 08:47:32
tags:
 - css
 - problem
categories:
 - problem
 - css
---

# 清除text-indent对img的影响

今天在处理富文本样式的时候遇到一个问题，当给`p`标签设置了`text-indent`后，`p`标签下的`img`标签也会收到此属性的影响而前面出现空隙。如下图所示：

![image-20220614090313479](https://object-srote-1305109524.cos.ap-beijing.myqcloud.com/img/image-20220614090313479.png)

经过一番查找后发现，只需给`img`标签设`display: block`（除了带有`inline`的属性就可以，也就是说只要使得元素不再是行内元素即可）或`float`也可以。

除此之外，在前辈老哥的提醒下，在处理富文本样式的时候不可直接使用标签作为选择器，这样会导致样式的污染，应当使用`class`类来进行样式的约束。😁
