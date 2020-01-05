---
layout: post
title: Go for Javaers
category: 读书
keywords: 阅读,书单
---

给Java程序猿的Go语言入门

使用Go的项目
Docker
Kubernets
lantern
gogs
grafana
etcd
influxdb
caddy
beego

赋值
i := 1 // var i int = 1
const A int = 100 // 不能用 :=

var i, j int = 1, 2
var i, j = true, "aa" // i bool; j string

var(
    i int = 1
    B string
)
const(
    i int = 1
    B = "hello" // B string
)

字符串类型
占用1~4字节
str[i]只对纯ASCII码的字符串有效

两个包：strings, strconv

解释字符串：双引号, "\n" 转义
非解释字符串：反引号, `\n` 原样输出

字符串的修改
str := "hello world"
str2 := "亚瑟王"

strArr := []byte(str)
strArr[0] = 'X'
fmt.Println(str)
fmt.Println(string(strArr))

strArr:= []rune(str2) //优先使用
strArr[0] = 'w'
fmt.Println(str2)
fmt.Println(string(strArr))

strArr:= []byte(str2) //取不全
strArr[0] = 'w'
fmt.Println(str2)
fmt.Println(string(strArr))


字符串拼接
加号 + 拼接
strings.join
bytes.Buffer

var buffer bytes.Buffer
buffer.WriteString("hello")
fmt.Println(buffer.String()) //顾名思义，使用buffer，类似于StringBuilder

字符串遍历
str = "hello 世界"
for i, n := 0, len(str); i < n; i++ {
	var ch2 byte = str[i]
	fmt.Printf("%d - %c , ", i, ch2)
}

for i, ch := range str {
	fmt.Printf("%d: %v, %c \n", i, ch, ch) // ch 是 rune类型
	// fmt.Printf("%c .", ch)
}