---
layout: post
title: Go for Javaers -- Pointer
category: 读书
keywords: 阅读,书单
---

给Java程序猿的Go语言入门 -- Pointer

* 星号
定义&取值

& 取地址

*& 抵消
var a int = 1       // int value
var b *int = &a     // int指针，指向int a的指针，存int a地址 (内存1)
var c **int = &b    // int指针的指针，指向int* b的指针，存int* b的地址 (内存2)
var x int = *b      // int value，存指针b指向的值，也就是int a的值

fmt.Println("a = ", a)  // 1
fmt.Println("&a = ", &a) // 内存1
fmt.Println("*&a = ", *&a) // 1
fmt.Println("b = ", b) // 内存1
fmt.Println("&b = ", &b) // 内存2
fmt.Println("*&b = ", *&b)// 内存1
fmt.Println("*b = ", *b)//1
fmt.Println("c = ", c)// 内存2
fmt.Println("*c = ", *c)// 内存1
fmt.Println("&c = ", &c)// 内存3 指向指针的指针的地址
fmt.Println("*&c = ", *&c)// 内存2
fmt.Println("**c = ", **c)//1
fmt.Println("***&*&*&*&c = ", ***&*&*&*&*&c) //1
fmt.Println("x = ", x)//1

swap
var a = 3
var b = 4
swap(&a, &b)
fmt.Println(a, b)

func swap(a *int, b *int) {
	//x := *a
	//*a = *b
	//*b = x
	*a, *b = *b, *a
}


