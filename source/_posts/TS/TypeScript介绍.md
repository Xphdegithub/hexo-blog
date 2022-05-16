---
title: TypeScript介绍
date: 2022-05-07 20:19:28
tags: TypeScript
categories:
  - 前端
  - TypeScript
---

# TypeScript介绍

`TypeScript`是`JavaScript`的超集，是一个可选的、静态的**类型系统**（对代码中所有的表示福【变量、函数、参数、返回值】进行类型检查）。

## TypeScript的特点💪

- 可选的

  顾名思义，爱用不用😛

- 静态的

  无论是`node`环境还是浏览器环境，都无法直接识别`TS`代码（需要使用`tsc`进行转换）

  `TS`代码 ---> `tsc`转换 ---> `JS`代码

  静态既类型检查发生在转换过程中，所以`TS`不参与代码的运行

## TypeScript的安装💠

```
yarn global add typescript
```
