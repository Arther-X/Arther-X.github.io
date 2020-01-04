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

TODO 字符串的修改
