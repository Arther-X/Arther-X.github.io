---
layout: post
title: Go101阅读笔记 -- 协程、延迟函数调用、以及恐慌和恢复(2)
category: 读书
keywords: 阅读,书单
---

Go101阅读笔记 -- 协程、延迟函数调用、以及恐慌和恢复(2) 并发同步

Go支持几种并发同步技术，其中通道是最独特和最常用的。
这里我们将使用sync标准库包中的WaitGroup来同步上面这个程序中的主协程和两个新创建的协程。
WaitGroup类型有三个方法（特殊的函数，将在以后的文章中详解）：Add、Done和Wait
```
package main

import (
	"log"
	"math/rand"
	"time"
	"sync"
)

var wg sync.WaitGroup

func SayGreetings(greeting string, times int) {
	for i := 0; i < times; i++ {
		log.Println(greeting)
		d := time.Second * time.Duration(rand.Intn(5)) / 2
		time.Sleep(d)
	}
	wg.Done() // 通知当前任务已经完成。
}

func main() {
	rand.Seed(time.Now().UnixNano())
	log.SetFlags(0)
	wg.Add(2) // 注册两个新任务。
	go SayGreetings("hi!", 10)
	go SayGreetings("hello!", 10)
	wg.Wait() // 阻塞在这里，直到所有任务都已完成。
}
```
