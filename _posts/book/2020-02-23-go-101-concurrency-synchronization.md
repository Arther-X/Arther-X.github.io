---
layout: post
title: Go101阅读笔记 -- 协程、延迟函数调用、以及恐慌和恢复(4)
category: 读书
keywords: 阅读,书单
---

Go101阅读笔记 -- 协程、延迟函数调用、以及恐慌和恢复(4) 延迟函数调用
deferred function call
一个函数调用可以跟在一个defer关键字后面，形成一个延迟函数调用。 和协程调用类似，被延迟的函数调用的所有返回值必须全部被舍弃。
当一个函数调用被延迟后，它不会立即被执行。它将被推入由当前协程维护的一个延迟调用堆栈。 当一个函数调用（可能是也可能不是一个延迟调用）返回并进入它的退出阶段后，所有在此函数调用中已经被推入的延迟调用将被按照它们被推入堆栈的顺序逆序执行。 当所有这些延迟调用执行完毕后，此函数调用也就真正退出了。

```
package main

import "fmt"

func main() {
	defer fmt.Println("The third line.")
	defer fmt.Println("The second line.")
	fmt.Println("The first line.")
}
```

输出
```
The first line.
The second line.
The third line.
```



