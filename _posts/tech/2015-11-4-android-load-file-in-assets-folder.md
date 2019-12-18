---
layout: post
title: Android记载assets文件夹下的文件
category: 技术
tags: Head first Android
keywords: 
description: 
---



Android加载assets文件夹下的文件

几个关键点
AssetManager  InputStream  (Properties)
activity

```
AssetManager assetManager = activity.getResources().getAssets();
InputStream fileIn = assetManager.open("FILE_NAME");

// properties文件操作，并不是关键点
Properties prop = new Properties();
prop.load(fileIn); // 从流中读取
Log.d(TAG, prop.getProperty("STRING_KEY"));
//

fileIn.close(); // 记得关闭流

```
