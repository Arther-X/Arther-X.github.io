---
layout: post
title: Go101阅读笔记 -- 简介
category: 读书
keywords: 阅读,书单
---

Go101阅读笔记 -- 简介
2019-12-29 09:30:39

《Go语言101》是一本着墨于Go语法和语义的编程指导书（Go 1.13就绪）。 这本书也搜集了很多Go编程中的的细节和讲解了一些底层实现原理（不含具体实现细节）。 这本书的宗旨是尽量帮助Go程序员更深和更全面地理解Go。 此书同时适合Go初学者和有一定经验的Go程序员阅读。

本书由老貘编写，隔空在此感谢作者的分享，这本书算是我go语言入门的启蒙教材了。

Go属于编译型的静态语言,但是Go的很多特性使得用Go编程像使用动态脚本语言一样的灵活。

Go标准编译器 - gc (是Go compiler的缩写，不是垃圾回收garbage collection的缩写)，支持跨平台编译
PS: 官方还有维护另一个编译器，gccgo

Go语言的一些特性
    1)内置并发编程支持：
        使用协程（goroutine）做为基本的计算单元。轻松地创建协程。
        使用通道（channel）来实现协程间的同步和通信。
    2)内置了映射（map）和切片（slice）类型。
    3)支持多态（polymorphism）。
    4)使用接口（interface）来实现裝盒（value boxing）和反射（reflection）。
    5)支持指针。
    6)支持函数闭包（closure）。
    7)支持方法。
    8)支持延迟函数调用（defer）。
    9)支持类型内嵌（type embedding）。
    10)支持类型推断（type deduction or type inference）。
    11)内存安全。
    12)自动垃圾回收。
    13)良好的代码跨平台性。




