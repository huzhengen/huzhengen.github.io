---
layout: post
title:  "HTTP基础"
date:   2018-10-09 10:33:21
categories: http
excerpt: HTTP基础
---

* content
{:toc}

# HTTP基础

本文主要介绍三个内容

* HTTP 请求包括哪些部分，如何用Chrome开发者工具查看 HTTP 请求内容
* HTTP 响应包括哪些部分，如何用Chrome开发者工具查看 HTTP 响应内容
* 如何使用 curl 命令

**一、HTTP 请求包括哪些部分，如何用Chrome开发者工具查看 HTTP 请求内容**

HTTP请求包括4部分

1、动词 路径 协议/版本

2、Key: value

3、（回车\n）

4、要上传的数据

比如GET请求：

打开Chrome，按F12，点击Network，在地址栏输入网址（比如https://www.baidu.com），点击第一个，然后查看右面的Headers里的**Request Headers**，点击view source，即可看到。

![http1.png](/static/images/http1.png)

![http2.png](/static/images/http2.png)

GET / HTTP/1.1

Host: www.baidu.com

Connection: keep-alive

Upgrade-Insecure-Requests: 1

User-Agent: Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36

> 第3部分没有显示，没有第4部分

POST请求：

POST /v2/api/?login HTTP/1.1

Host: passport.baidu.com

Connection: keep-alive

> 第3部分没有显示，第4部分在Form Data里

**二、HTTP 响应包括哪些部分，如何用Chrome开发者工具查看 HTTP 响应内容**

HTTP响应包括4部分

1、协议/版本号 状态码 状态解释

2、Key: value

3、（回车\n）

4、要下载的内容

打开Chrome，按F12，点击Network，在地址栏输入网址（比如https://www.baidu.com），点击第一个，然后查看右面的Headers里的**Response Headers**，点击view source，即可看到。

![http3.png](/static/images/http3.png)

![http4.png](/static/images/http4.png)

HTTP/1.1 200 OK

Bdpagetype: 2

Cache-Control: private

Connection: Keep-Alive

Content-Encoding: gzip

Content-Type: text/html;charset=utf-8

> 第3部分没有显示，第4部分在Headers右边的右边Response里

**三、如何使用 curl 命令**

在命令行输入`curl -s -v -H "username: tom" -- "https://www.baidu.com"`

返回

![curl1.png](/static/images/curl1.png)

-s/--slient 静默模式

-v/--verbose 显示请求详细信息

-H/--header 增加头部信息

[curl英文文档](https://curl.haxx.se/docs/manpage.html)