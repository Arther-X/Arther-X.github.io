---
layout: post
title: Java 线程池
category: 技术
tags: java more
keywords: 
description: 
---


准备写一篇关于研究线程池的文
行文思路大致分为三大块

1.线程池相关概念，深究。（可以考虑涉及到操作系统层面）
2.自己的实现。（这个需求源码，放到Git上面）
3.当前成熟的实现（现在准备写的是JDK的，Apache的）


学习过程中的一些小点，做一些记录
1.Worker因为是ThreadPoolExecutor内部类，Worker.run方法调用的是ThreadPoolExecutor.runWorker方法。
  这种写法挺新颖的
2.看ThreadPoolExecutor.getTask方法的时候，发现了retry:关键字。
  这个标示，居然是用来告诉虚拟机代码从哪里开始运行的。。。一般会配合continue retry;来使用
  
3.序列化接口，不含有任何方法，只是用于标识类可以序列化。
  这个设计挺新颖的，我想看看具体实现上有什么好玩的东西



