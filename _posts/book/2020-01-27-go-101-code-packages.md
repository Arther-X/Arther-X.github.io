---
layout: post
title: Go101阅读笔记 -- 代码包和包引入
category: 读书
keywords: 阅读,书单
---

Go101阅读笔记 -- 代码包和包引入

包引用
```
package main

import "fmt"
import "math/rand"


func main() {
	fmt.Println("Go has", 25, "keywords.")
    fmt.Printf("下一个伪随机数总是%v。\n", rand.Uint32())

}
```
第一行指定了源文件simple-import-demo.go所处的包名为main。 程序入口main函数必须处于一个名为main的代码包中。
第三行通过使用import关键字引入了fmt标准库包。 在此源文件中，fmt标准库包将用fmt标识符来表示。 标识符fmt称为fmt标准库包的引入名称。（后续某节将详述代码包的引入名称）。
fmt标准库包中声明了很多终端打印函数供其它代码包使用。 Println函数是其中之一。 它可以将不定数量参数的字符串表示形式输出到标准输出中。 第六行调用了此Println函数。 注意在此调用中，函数名之前需要带上前缀fmt.，其中fmt是Println函数所处的代码包的引入名称。 aImportName.AnExportedIdentifier这种形式称为一个限定标识符（qualified identifier）。
fmt.Println函数调用接受任意数量的实参并且对实参的类型没有任何限制。 所以此程序中的此函数调用的三个实参的类型将被推断为它们各自的默认类型：string、int和string。
对于一个fmt.Println函数调用，任何两个相邻的实参的输出之间将被插入一个空格字符，并且在最后将输出一个空行字符。

math/rand标准库包的引入名是rand。 rand.Uint32()函数调用将返回一个uint32类型的随机数。
Printf函数是fmt标准库包中提供的另外一个常用终端打印函数。 一个Printf函数调用必须带有至少一个实参，并且第一个实参的类型必须为string。 此第一个实参指定了此调用的打印格式。此格式中的%v在打印结果将被对应的后续实参的字符串表示形式所取代。 比如上列中的%v在打印结果中将被rand.Uint32()函数调用所返回的随机数所取代。 打印格式中的\n表示一个换行符，这在基本类型和它们的字面量表示一文中已经解释过。
