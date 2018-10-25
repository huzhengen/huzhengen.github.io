---
layout: post
title:  "JS 里的数据类型转换"
date:   2018-10-25 13:32:16
categories: javascript
excerpt: JS 里的数据类型转换
---

* content
{:toc}

# JS 里的数据类型转换

JS里的数据类型转换一般包括`转为字符串`、`转为数字`、`转为布尔值`

### 转为字符串

转为字符串的方法包括：`toString()`、`与空字符串''相加`、`用全局函数window.String()`

```js
String(123) // "123" 数字转为字符串
String('abc') // "abc" 字符串转为字符串
String(true) // "true" 布尔值转为字符串
String(undefined) // "undefined" undefined转为字符串
String(null) // "null" null转为字符串
String({a: 1}) // "[object Object]" 对象转为字符串
String([1, 2, 3]) // "1,2,3" 数组转为字符串
```

### 转为数字

转为数字的方法包括：`Number()`、`parseInt()`、`parseFloat()`、`字符串-0`、`+字符串`

```js
Number(123) // 123 数字转为数字
Number('321') // 321 可以被解析为数字的字符串转为数字
Number('123abc') // NaN 不能被解析为数字的字符串转为数字
Number('abc123') // NaN 不能被解析为数字的字符串转为数字
Number('') // 0 空字符串转为数字
Number(true) // 1 布尔值true转为数字
Number(false) // 0 布尔值false转为数字
Number(undefined) // NaN undefined转为数字
Number(null) // 0 null转为数字
Number({a: 1}) // NaN 对象转为数字
Number([1, 2, 3]) // NaN 数组转为数字
Number([5]) // 5 包含单个数值的数组转为数字
```

parseInt()和Number()有一些不同

```js
parseInt(123) // 123 数字转为数字
parseInt('321') // 321 可以被解析为数字的字符串转为数字
parseInt('123abc') // 123 不能被解析为数字的字符串转为数字
parseInt('abc123') // NaN 不能被解析为数字的字符串转为数字
parseInt({a: 1}) // NaN 对象转为数字
parseInt([1, 2, 3]) // 1 数组转为数字
parseInt([5]) // 5 包含单个数值的数组转为数字
```

### 转为布尔值

转为布尔值的方法包括：`Boolean()`、`!!`

falsy值：总共有5个falsy值：`0`、`NaN`、`''`、`null`、`undefined`。

```js
Boolean(0) // false
Boolean(NaN) // false
Boolean('') // false
Boolean(null) // false
Boolean(undefined) // false
```

其它的值全都是true。（空对象、空数组也是true）

### 四个关于内存图的题目

简单数据类型的值直接存在Stack栈内存中，复杂数据类型（object）的值在Stack栈内存中存Heap地址。

1、

```js
var a = 1
var b = a
b = 2
console.log(a) // 1
```

2、

```js
var a = {name:'allen'}
b = a
b = {name: 'bruce'}
console.log(a.name) // allen
```

3、

```js
var a = {name: 'allen'}
var b = a
b.name = 'bruce'
console.log(a.name) // bruce
```

4、

```js
var a = {name: 'allen'}
var b = a
b = null
console.log(a) // {name: 'allen'}
```