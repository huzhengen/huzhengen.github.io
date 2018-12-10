---
layout: post
title:  "初识cookie"
date:   2018-12-10 15:14:29
categories: cookie 前端
excerpt: 初识cookie
---

* content
{:toc}

# 初识cookie

### 先说下简单的注册登录的过程

1、注册。用户打开注册页面，输入注册信息后，点击注册，发送POST请求，服务器收到后会写入数据库，通知用户注册成功。

2、登录。用户打开登录页面，输入登录信息后，点击登录，发送POST请求，服务器收到信息后，和数据库中的信息对比，符合则表示成功，这时候服务器可以设置cookie，通知用户登录成功。（这时候用户再打开该域名网站时，请求头会带上cookie，服务器会根据cookie在数据库查到该用户，这样就可以在网站页面展示该用户的一些信息。）

### 服务端设置cookie

原生 nodejs 设置cookie

```js
let http = require('http')
let server = http.createServer(function(request, response) {
	let path = request.url
	if (path === '/sign_in' && method === 'POST') {
		response.setHeader('Set-Cookie', `sign_in_email=${email}`)
	}
})
server.listen(port)
```

Express 设置设置cookie

```js
const express = require('express')
const app = express()

app.get('/', (req, res) => {
  res.header('Set-Cookie', ['name=lucy', 'age=20'])
  res.send('Hello World!')
})

app.listen(3000)
```