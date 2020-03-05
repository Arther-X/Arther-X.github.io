---
layout: post
title: Go101阅读笔记 -- Go类型系统概述 - 精通Go编程必读
category: 读书
keywords: 阅读,书单
---

Go101阅读笔记 -- Go类型系统概述 - 精通Go编程必读


基本类型（basic type）
内置字符串类型：string.
内置布尔类型：bool.
内置数值类型：
int8、uint8（byte）、int16、uint16、int32（rune）、uint32、int64、uint64、int、uint、uintptr。
float32、float64。
complex64、complex128。
注意，byte是uint8的一个内置别名，rune是int32的一个内置别名。 下面将要提到如何声明自定义的类型别名。

组合类型（composite type）
Go支持下列组合类型：
指针类型 - 类C指针
结构体类型 - 类C结构体
函数类型 - 函数类型在Go中是一种一等公民类别
容器类型，包括:
数组类型 - 定长容器类型
切片类型 - 动态长度和容量容器类型
映射类型（map）- 也常称为字典类型。在标准编译器中映射是使用哈希表实现的。
通道类型 - 通道用来同步并发的协程
接口类型 - 接口在反射和多态中发挥着重要角色


事实：类型的种类
每种上面提到的基本类型和组合类型都对应着一个类型种类（kind）。除了这些种类，今后将要介绍的非类型安全指针类型属于另外一个新的类型种类。

所以，目前（Go 1.14），Go有26个类型种类。

语法：类型定义（type definition declaration）
（类型定义又称类型定义声明。在Go 1.9之前，类型定义被称为类型声明并且是唯一的一种类型声明形式。 但是自从Go 1.9，类型定义变成了两种类型声明形式之一。另一种新的类型声明形式为下一节将要介绍的类型别名声明。）

在Go中，我们可以用如下形式来定义新的类型。在此语法中，type为一个关键字。
```
// 定义单个类型。
type NewTypeName SourceType

// 定义多个类型。
type (
	NewTypeName1 SourceType1
	NewTypeName2 SourceType2
)
```

