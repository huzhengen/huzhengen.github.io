---
layout: post
title:  "JavaScript data type Symbol"
date:   2023-05-10 19:26:29 +0800
categories: javascript
excerpt: Symbol is a primitive data type in JavaScript that was introduced in ECMAScript 6 (ES6). It is used to create unique identifiers that are not visible to the rest of the program. Symbols are immutable and unique, meaning that once a symbol is created, it cannot be changed, and every symbol created is different from every other symbol.
---

* content
{:toc}

JavaScript data type Symbol

Symbol is a primitive data type in JavaScript that was introduced in ECMAScript 6 (ES6). It is used to create unique identifiers that are not visible to the rest of the program. Symbols are immutable and unique, meaning that once a symbol is created, it cannot be changed, and every symbol created is different from every other symbol.

To create a symbol in JavaScript, you can use the Symbol() constructor, like this:

```js
const mySymbol = Symbol();
```

You can also provide a description to a symbol, which can be useful for debugging purposes:

```js
const mySymbol = Symbol('my description');
```

Symbols are often used as property keys in objects, as they cannot clash with any other property keys. For example:

```js
const myObj = {
  [Symbol('key1')]: 'value1',
  [Symbol('key2')]: 'value2'
};
```

To access the values of these properties, you need to use the bracket notation:

```js
console.log(myObj[Symbol('key1')]); // undefined
console.log(myObj[Object.getOwnPropertySymbols(myObj)[0]]); // 'value1'
```

The first console.log statement returns undefined because a new symbol is being created and is not the same as the one used as the property key. The second console.log statement uses the Object.getOwnPropertySymbols() method to retrieve the array of symbols used as keys in the object, and then accesses the first symbol to retrieve the value associated with it.

Symbols can also be used to define private properties or methods in classes, as they cannot be accessed from outside the class. For example:

```js
class MyClass {
  #privateProperty = Symbol('private property');
  
  getPrivateProperty() {
    return this[this.#privateProperty];
  }
}

const myInstance = new MyClass();
myInstance.#privateProperty // Error: privateProperty is not accessible from outside the class
```

Here, the #privateProperty symbol is used to define a private property in the MyClass class. The getPrivateProperty() method can access the private property, but it cannot be accessed from outside the class.

In conclusion, symbols are a powerful addition to the JavaScript language that allow for the creation of unique identifiers and private properties and methods. Although they are not commonly used, they can be very useful in certain situations where uniqueness and privacy are important.


