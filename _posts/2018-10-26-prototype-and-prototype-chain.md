---
layout: post
title:  "原型与原型链"
date:   2018-10-26 10:15:18
categories: javascript 前端
excerpt: 原型与原型链
---

* content
{:toc}

# 原型与原型链

[先去谷歌翻译查询**原型**的英文是什么。谷歌翻译显示原型的常见译文为prototype](https://translate.google.com/#zh-CN/en/%E5%8E%9F%E5%9E%8B)

### 关于原型

比如下面这个代码

```js
var n1 = new Number('123')
console.log(n1)
```

这个代码你可以自己运行一下，打印出来n1，看看结果是什么，我在浏览器控制台Console里打印出来的结果是一个对象，包括

```js
__proto__: Number // 这个还是一个对象
[[PrimitiveValue]]: 123
```

这里说一个例子，比如要转成字符串，那么可以用toString()方法，即n1.toString()，n1后面的这个点.表示n1的属性或者方法

但是看上面打印出来的n1，并没有toString，而我们运行n1.toString()是会顺利得到结果的，那么这个toString在哪呢？

答案就是toString方法在`n1.__proto__`里面，而这里的`n1.__proto__`有一个指向/引用，指向的是Number的prototype（prototype翻译为中文：原型），这个就是原型。即：n1的原型是Number.prototype。

```js
n1.__proto__ === Number.prototype // true
```

> 阮一峰JavaScript教程里写到：读取对象的某个属性时，JavaScript 引擎先寻找对象本身的属性，如果找不到，就到它的原型去找，如果还是找不到，就到原型的原型去找。如果直到最顶层的Object.prototype还是找不到，则返回undefined。如果对象自身和它的原型，都定义了一个同名属性，那么优先读取对象自身的属性，这叫做“覆盖”（overriding）。

### 原型链

还是用这个代码举例

```js
var n1 = new Number('123')
```

这行代码我们可以把他改写成

```js
var 对象x = new 函数y([参数z])
```

那么根据上面讲解的，可以得出来：

```js
对象x.__proto__ === 函数y.prototype
对象x的原型就是函数y.prototype
```

> 阮一峰的JavaScript教程里写到：JavaScript 规定，所有对象都有自己的原型对象（prototype）。一方面，任何一个对象，都可以充当其他对象的原型；另一方面，由于原型对象也是对象，所以它也有自己的原型。因此，就会形成一个“原型链”（prototype chain）：对象到原型，再到原型的原型……

代入阮一峰讲的原型链

1、一方面，任何一个对象，都可以充当其他对象的原型；

对应上面的代码就是：`函数y的prototype`这个对象，是`对象x`的原型

2、另一方面，由于原型对象也是对象，所以它也有自己的原型。

对应代码：`对象x的原型`是一个对象，即`函数y的prototype`是一个对象，那么它的原型是什么呢？

这时候就可以寻找`函数y的prototype`的`__proto__`，即：

```js
函数y.prototype.__proto__ === Object.prototype
```

那么`Object.prototype`的原型呢？即：

```js
Object.prototype.__proto__ === null
```

### 参考来源：

https://wangdoc.com/javascript/oop/prototype.html