---
layout: post
title: 【Kubernetes in action】info
category: 技术
tags: k8s k8sia
keywords: K8S
description: 
---

写在前面
Kubernetes，一般简写为k8s。18年初了解到Gou家的k8s，是因为有计划将创业项目改成microservice。
之前想着写一些文章，不一直比较忙。最近正好有时间，以前的老github账号充公了，正好借着翻新博客的机会也翻新一下自己，给人生的前1/3画个句号。
后续会逐步更新系列文章，除了事件系列，还有会有k8s源码阅读等，也争取翻译一些好的相关技术文章。

【Kubernetes in action】系列文章 一 基础概念
Docker
Kubernetes
microservice

在保守 Borg 和 Omega 秘密数十年之后， 2014 年 ， 谷歌开放了 Kubernetes, 个基于Borg、 Omega及其他谷歌内部系统实践的开源系统。
Kubernetes 是 一 个软件系统，它允许你在其上很容易地 部署 和 管理容器应用

master
主节点 ，它承载着 Kubernetes控制和管理整个集群系统的控制面板
    Kubernets API服务器
    Scheculer
    Controller Manager
    etcd

worker
工作节点，它们运行用户实际部署的应用
    Docker or rtk
    Kubelet
    Kubernets Service Proxy(kube-proxy)

2019-12-22
这两天快圣诞，除了做一些h3相关的以及google api的研究以外，都没怎么顾得上。
明天开始就有时间了

2019-12-23
发现一个新的项目叫k3s
还有国内好像对service mesh比较感兴趣

2019-12-25 
今天圣诞节，偷个小懒，暂时没有更新。
后半夜会先把h3相关的数据处理成lan&long，有空再看看书，争取明天9点起来boxing day

2019-12-30 22:24:26
knative

2020-01-01 23:24:01
