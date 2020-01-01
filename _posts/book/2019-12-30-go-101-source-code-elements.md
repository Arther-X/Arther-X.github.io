---
layout: post
title: Go 101
category: 读书
keywords: 阅读,书单
---

Go101阅读笔记 -- 源代码基本元素

关于代码断行
很多左大括号 { 不能被放到下一行。

分号
正式的Go语法是使用（英文）分号;做为结尾标识符的。 
但是，我们很少在Go代码中使用和看到分号。
大多数分号都是可选的，因此它们常常被省略。 在编译时刻，Go编译器会自动插入这些省略的分号。
(TODO Go Programming Language Specification)

关键字
1)
const、func、import、package、type和var用来声明各种代码元素。

2)
chan、interface、map和struct用做 一些组合类型的字面表示中。

3)
break、case、continue、default、else、fallthrough、for、goto、if、range、return、select和switch用在流程控制语句中。 详见基本流程控制语法。

4)
defer和go也可以看作是流程控制关键字， 但它们有一些特殊的作用。详见协程和延迟函数调用。

基本内置类型
布尔型: bool
字符串: string
11种内置整数类型:
    int8、uint8(byte)、int16、uint16、int32(rune)、uint32、int64、uint64、
    int、uint和uintptr。
2种内置浮点数类型:
    float32和float64。
2种内置复数类型:
    complex64和complex128。

(TODO 范围 https://gfw.go101.org/article/basic-types-and-value-literals.html)







