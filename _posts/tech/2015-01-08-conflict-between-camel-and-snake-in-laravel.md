---
layout: post
title: ThreadLocal源码——JDK中如何实现为每一个使用该变量的线程都提供一个变量值的副本
category: 技术
tags: [java, thread]
keywords: 
description: 
---

说好的技术博客，现在就来第一篇

最近一段时间在把一个本地工具搭成web版本，进行一些封装，针对一些业务功能还要进行在开发。用到一些并发模型，涉及一点线程。陆陆续续会更新编写过程中遇到、用到、学到的东西。

这篇主要说一下**ThreadLocal**。

网上有很多ThreadLocal的使用教程，也都提到ThreadLocal为每个使用该变量的线程提供独立的变量副本，而不会影响到其他线程。讲到实现原理的时候，都提到说：
**JDK中ThreadLocal类中有一个Map，key是线程对象，valute为对应线程的变量副本。**

我想说，这是完全错误的。。。
其实，从JDK1.2版本开始，ThreadLocal的实现原理就不是这样的。
真实的情况是，每一个Thread内，都会有一个ThreadLocalMap用来存放自己用到的ThreadLocal，key为ThreadLocal实例，value为使用时set进去的对象。

我们从源码的角度来分析（使用jdk1.7版本）
首先来看ThreadLocal的set方法

```
java.lang.ThreadLocal
    public void set(T value) {
        Thread t = Thread.currentThread();//取到当前线程，native方法
        ThreadLocalMap map = getMap(t);//我想误解应该是从这句开始的，后面会详细说
        if (map != null)
            map.set(this, value);//key为ThreadLocal，value为set进来的对象
        else
            createMap(t, value);
    }
```
乍一看是通过当前线程t取到了ThreadLocalMap，其实是从t中取到ThreadLocalMap对象，我们看一眼getMap(t)方法的实现就清楚了。

```
java.lang.ThreadLocal
    ThreadLocalMap getMap(Thread t) {
        return t.threadLocals;
    }
```

```
java.lang.Thread
    ThreadLocal.ThreadLocalMap threadLocals = null;
```

这就是ThreadLocal为什么会是每个线程单独拥有的。
在每个Thread中会有一个ThreadLocalMap，当我们调用某一个ThreaLocal实例的set方法时，会去当前Thread中取ThreadLocalMap，使用ThreadLocal实例为key，将set进来的值作为value存储在map中。



*The end*

另附createMap方法


```java.lang.ThreadLocal
    void createMap(Thread t, T firstValue) {
        t.threadLocals = new ThreadLocalMap(this, firstValue);
    }
```


PS：ThreadLocalMap也挺有意思，他是一个被标示为static的内部类，核心是Entry[]，Entry也为static，继承自WeakReference<ThreadLocal>。

