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

协程的状态
一个活动中的协程可以处于两个状态：运行状态和阻塞状态。
一个处于睡眠中的（通过调用time.Sleep）或者在等待系统调用返回的协程被认为是处于运行状态，而不是阻塞状态。
当一个新协程被创建的时候，它将自动进入运行状态，一个协程只能从运行状态而不能从阻塞状态退出。 如果因为某种原因而导致某个协程一直处于阻塞状态，则此协程将永远不会退出。
当一个程序死锁后，官方标准编译器的处理是让这个程序崩溃。

逻辑CPU数
用runtime.NumCPU函数来查询当前程序可利用的逻辑CPU数目。 
每个逻辑CPU在同一时刻只能最多执行一个协程。Go运行时（runtime）必须让逻辑CPU频繁地在不同的处于运行状态的协程之间切换，从而每个处于运行状态的协程都有机会得到执行。 这和操作系统执行系统线程的原理是一样的。

标准编译器采纳了一种被称为M-P-G模型的算法来实现协程调度。
M表示系统线程，P表示逻辑处理器（并非上述的逻辑CPU），G表示协程。
大多数的调度工作是通过逻辑处理器（P）来完成的。 逻辑处理器像一个监工一样通过将不同的处于运行状态协程（G）交给不同的系统线程（M）来执行。
一个协程在同一时刻只能在一个系统线程中执行。一个执行中的协程运行片刻后将自发地脱离让出一个系统线程，从而使得其它处于等待子状态的协程得到执行机会。
