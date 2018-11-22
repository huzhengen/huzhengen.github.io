---
layout: post
title:  "小程序打开的时候获取app.globalData为空"
date:   2018-11-22 13:46:29
categories: 小程序
excerpt: 小程序打开的时候获取app.globalData为空
---

* content
{:toc}

# 小程序打开的时候获取app.globalData为空

> 该博客只适合本人，我写的很简单，别人有可能看不懂描述。

小程序授权后重新打开页面有可能获得app.globalData为空

google后没有搞明白到底怎么写才ok

我自己想了个办法，一开始授权的时候用wx.setStorageSync存入缓存，以后再开页面的时候用wx.getStorage获取缓存

> 注意这里用的是wx.setStorageSync，而不是wx.setStorage