---
title: TypeScript配置文件
date: 2022-05-07 20:31:41
tags: TypeScript
categories:
  - 前端
  - TypeScript
---

# TypeScript配置文件⚙

默认情况下，`TS`会做出以下假设

- 假设当前执行的环境是`dom`
- 如果代码中没有会用模块化语句（`import`、`export`），便认为该代码是全局执行
- 编译的目标代码时`ES3`

有两种方法可以更改以上假设:

1. 使用`tsc`命令执行的时候，加上选项参数
2. 使用`ts`配置文件，更改编译选项（推荐使用）

`Ts`的配置文件为`tsconfig.json`，可直接创建，也可使用命令`tsc --init`创建

```json
{
	"compilerOptions": { // 编译选项
        "target": "es2016",  // 编译目标代码的版本标准
        "module": "commonjs", // 编译目标使用的模块化标准
        "lib": ['es2016'], // 编译目标当前的环境/全局可使用的变量
        "outDir": "./dist", // 输出目录
        "strictNullChecks": true, // 不可将undefined和null赋值
        "removeComments": true, // 表示编译的结果中移除注释
        "stricPropertyInitialization": true, // 以更加严格的方式来检查值得初始化
    },
    "include": ["./src"], // 编译路径
    "files": ["./src/index.ts"], // 编译单个文件及其依赖文件
}
```

注意🔥:

 1. 使用`TS`配置文件后，在使用`tsc`命令编译时，后面不能跟文件名，若跟了会忽略配置文件

 2. `TS`默认没有`node`环境，所以需要安装`@types/node`，`@types`是一个官方的类型吗描述库，，其中包含了很多对`js`代码的类型描述

    举个栗子🌰:

    `JQuery`使用`JS`写的，但是`TS`默认没有对他的类型检查

    安装`@types/jquery`为`jquery`库添加类型定义
