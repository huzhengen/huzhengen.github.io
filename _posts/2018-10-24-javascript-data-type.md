---
layout: post
title:  "JS 里的数据类型"
date:   2018-10-24 14:03:43
categories: javascript
excerpt: JS 里的数据类型
---

* content
{:toc}

# JS 里的数据类型

JavaScript有7种数据类型，包括数字（number）、字符串（string）、布尔（boolean）、undefined（undefined）、null（null）、对象（object）和Symbol（Symbol）。

* 数字（number）

    包括十进制（11、12e3）、二进制（0b11。0b或者0B开头）、八进制（011。00或者0o开头，或者有前导0、且只用到0-7的八个阿拉伯数字）、十六进制（0x11。0x或者0X开头）。

    NaN是 JavaScript 的特殊值，表示“非数字”（Not a Number），主要出现在将字符串解析成数字出错的场合。

    ```js
    5 - 'x' // NaN
    ```

    NaN不等于任何值，包括它本身。

* 字符串（string）

    可以写在单引号`'`或者双引号`"`里，例如'abc'、"bbb"、''、' '。

    如果字符串里要有单引号`'`的话，可以用转义符号反斜杠，例如`'abc\'def\''`。

    字符串默认只能写在一行内，分成多行会报错，例如：

    ```js
    'a
    b
    c'
    // Uncaught SyntaxError: Invalid or unexpected token
    ```

    如果必须写成多行，可以用反斜杠（**反斜杠后面不能有空格**）

    ```js
    'a\
    b\
    c'
    ```

    或者用加号

    ```js
    'a'+
    'b'+
    'c'
    ```

    或者用ES6种新增的反引号

    ```js
    `a
    b
    c`
    ```

* 布尔（boolean）

    ture和false两个值

    一般用于流程控制语句

    ```js
    if(true){
        console.log('true')
    }
    ```

    关于逻辑运算符`&&`和`||`：

        * && 逻辑与：只有两个值都为true的时候，结果才为true，其余结果都是false。（有一个值是false，则结果就是false）

        * || 逻辑或：有一个值为true，结果就是true。

* null和undefined

    null类型的值为null，表示空值，undefined类型的值为undefined，表示未定义。

    这两个都表示什么也没有

    * null和undefined的区别：

        1、如果一个变量没有赋值，它就是undefined

        2、如果有一个对象object，现在还不想赋值，推荐给它null；如果是非对象，推荐初始化值为undefined。（惯例）

* 对象（object）

    简单说，对象就是一组“键值对”（key-value）的集合，是一种无序的复合数据集合。对象是复杂类型，复杂类型是由简单类型组成的。

    例子：

    ```js
    var person = {
        name: 'tom', // 对象的所有键名都是字符串（ES6 又引入了 Symbol 值也可以作为键名），所以加不加引号都可以。如果键名是数值，会被自动转为字符串。
        age: 18
    }
    ```

    读取对象的属性，有两种方法，一种是使用点运算符，还有一种是使用方括号运算符。

    ```js
    person.name // 使用点运算符
    person['age'] // 使用方括号运算符。如果使用方括号运算符，键名必须放在引号里面，否则会被当作变量处理。
    ```

    查看一个对象本身的所有属性，可以使用Object.keys方法。

    ```js
    Object.keys(person);
    ```

    delete命令用于删除对象的属性，删除成功后返回true。

    ```js
    delete person.name
    ```

    in运算符用于检查对象是否包含某个属性（注意，检查的是键名，不是键值），如果包含就返回true，否则返回false。

    ```js
    'age' in person // true
    ```

    for...in循环用来遍历一个对象的全部属性。

    ```js
    for(var key in person){
        console.log(key);
        console.log(person[key]);
    }
    ```

* Symbol

    Symbol 可以创建一个独一无二的值（但并不是字符串）。

    ```js
    var s = Symbol();
    ```

    Symbol函数可以接受一个字符串作为参数，表示对 Symbol 实例的描述，主要是为了在控制台显示，或者转为字符串时，比较容易区分。

    ```js
    var foo = Symbol('foo');
    var bar = Symbol('bar');
    foo === bar // false
    ```

判断一个值的数据类型可以用typeof运算符：

```js
function fn() {}
typeof 123 // "number"
typeof 'abc' // "string"
typeof false // "boolean"
typeof undefined // "undefined"
typeof null // "object"
typeof window // "object"
typeof {} // "object"
typeof [] // "object"
typeof fn // "function"
```