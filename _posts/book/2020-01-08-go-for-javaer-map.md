---
layout: post
title: Go for Javaers -- Map
category: 读书
keywords: 阅读,书单
---

给Java程序猿的Go语言入门 -- Map

创建
foo := map[int]string{1: "Peng Yuyan", 2: "Wu Yanzu"}
bar := make(map[string]string, 10)

查看
if v, ok := bar["title2"]; ok {
    fmt.Println(v)
}

删除
delete(bar, "name")

当map的value是数组时，修改value
https://stackoverflow.com/questions/38168329/why-are-map-values-not-addressable

// 重新赋值
foo := map[int][3]int{}
foo[1] = [3]int{1,2,3}
tmp := foo[1]
tmp[2] = 5
foo[1] = tmp  //重新赋值

// 指针的方式
foo := map[int]*[3]int{}  
foo[1] = &[3]int{1, 2, 3}
foo[1][2] = 6



