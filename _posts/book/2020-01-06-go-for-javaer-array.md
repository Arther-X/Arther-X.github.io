---
layout: post
title: Go for Javaers -- Array
category: 读书
keywords: 阅读,书单
---

给Java程序猿的Go语言入门 -- Array

声明，赋值
var arr1 [3]int // Java : int arr1[] = new int[3];

arr1 := [...]int{1,2,3} // arr1 := [3]int{1,2,3}
coder := [4]string{1:"aaa", 3:"ccc"}

arr2 := [3][4]int{
    {0,1,2,3},
    {4,5,6,7},// 最后一个逗号，不可缺失
    //最后一个行没有赋值，全部初始化为0
}

遍历
for i:=0; i<len(arr1); i++{
    fmt.Println(i, arr1[i])
}

for i, v:=range arr1 {
    fmt.Println(i, v)
}

函数内修改数组
指针数组，数组指针
ptrArr := [3]*int{1:new(int)} // 需要初始化
func change(a [3]*int) { // *在[]后面
    *a[1] = 233
}

arr1 := [...]int{1,2,3}
change(&arr1)
func change(a *[3]int) { // *在[]前面
    a[1] = 233
}
