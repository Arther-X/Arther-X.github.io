---
layout: post
title: Go101阅读笔记 -- 基本流程控制语法
category: 读书
keywords: 阅读,书单
---

Go101阅读笔记 -- 基本流程控制语法

if-else

```
if InitSimpleStatement; Condition {
	// do something
} else if condition {
} else {
	// do something
}

package main

import (
	"fmt"
	"time"
)

func main() {
	if h := time.Now().Hour(); h < 12 {
		fmt.Println("现在为上午。")
	} else if h > 19 {
		fmt.Println("现在为晚上。")
	} else {
		fmt.Println("现在为下午。")
		// 左h是一个新声明的变量，右h已经在上面声明了。
		h := h
		// 刚声明的h遮掩了上面声明的h。
		_ = h
	}

	// 上面声明的两个h在此处都不可见。
}

```

for
```
for InitSimpleStatement; Condition; PostSimpleStatement {
    // do something
}

for i := 0; i < 10; i++ {
	fmt.Println(i)
}

```

switch-case

```
switch InitSimpleStatement; CompareOperand0 {
case CompareOperandList1:
	// do something
case CompareOperandList2:
	// do something
...
case CompareOperandListN:
	// do something
default:
	// do something
}

package main

import (
	"fmt"
	"math/rand"
	"time"
)

func main() {
	rand.Seed(time.Now().UnixNano())
	switch n := rand.Intn(100); n%9 {
	case 0:
		fmt.Println(n, "is a multiple of 9.")

		// 和很多其它语言不一样，程序不会自动从一个
		// 分支代码块跳到下一个分支代码块去执行。
		// 所以，这里不需要一个break语句。
	case 1, 2, 3:
		fmt.Println(n, "mod 9 is 1, 2 or 3.")
		break // 这里的break语句可有可无的，效果
		      // 是一样的。执行不会跳到下一个分支。
	case 4, 5, 6:
		fmt.Println(n, "mod 9 is 4, 5 or 6.")
	// case 6, 7, 8:
		// 上一行行可能编译不过，因为6和上一个case中的
		// 6重复了。是否能编译通过取决于具体编译器实现。
    case 7:
        fallthrough
	default:
		fmt.Println(n, "mod 9 is 7 or 8.")
	}
}
```
fallthrough
一条fallthrough语句必须为一个分支代码块中的最后一条语句。
一条fallthrough语句不能出现在一个switch-case流程控制中的最后一个分支代码块中。
