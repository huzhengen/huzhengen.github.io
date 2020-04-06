---
layout: post
title:  "浅析 URL"
date:   2020-04-06 16:24:33
categories: url
excerpt: 浅析 URL
---

* content
{:toc}

# 浅析 URL

### URL

[什么是URL？](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/What_is_a_URL)

URL指的是统一资源定位符（Uniform Resource Locator）。

URL=协议+域名或IP+端口号+路径+查询字符串+锚点

一个URL的示例：`https://www.baidu.com/s?wd=hello&rsv_spt=1#5`

`https://`表示协议

`www.baidu.com`表示域名

`/s`表示路径

`?wd=hello&rsv_spt=1`标识查询参数

`#5`表示锚点

这里https端口号默认是443

### IP

[网际协议](https://zh.wikipedia.org/wiki/%E7%BD%91%E9%99%85%E5%8D%8F%E8%AE%AE)

网际协议（英语：Internet Protocol，缩写：IP；也称互联网协议）是用于分组交换数据网络的一种协议。

IP主要约定了2件事：
* 如何定位一台设备
* 如何封装数据报文，以跟其他设备交流

[ping](https://zh.wikipedia.org/wiki/Ping)

ping（呯）是一种计算机网络工具，用来测试数据包能否透过IP协议到达特定主机。

在命令行可以输入`ping baidu.com`，可以看到`baidu.com`对应的IP

### 域名

[域名](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D)

网域名称（英语：Domain Name，简称：Domain），简称域名、网域，是由一串用点分隔的字符组成的互联网上某一台计算机或计算机组的名称，用于在数据传输时标识计算机的电子方位。域名可以说是一个IP地址的代称，目的是为了便于记忆后者。

一个域名可以对应不同IP，这种技术叫做负载均衡，防止一台机器扛不住

一个IP可以对应不同的域名，这个叫做共享主机。

一般有一级域名（.com），二级域名（baidu.com），三级域名（fanyi.baidu.com）等

### DNS

[域名系统](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F)

域名系统（英语：Domain Name System，缩写：DNS）是互联网的一项服务。它作为将域名和IP地址相互映射的一个分布式数据库，能够使人更方便地访问互联网。

DNS可以把域名和IP联系起来