---
layout: post
title:  "JavaScript Data Types: Undefined"
date:   2023-05-09 14:26:19 +0800
categories: javascript
excerpt: In JavaScript, "undefined" is a primitive data type that represents a value that is not defined. It is used when a variable is declared but not initialized, or when a property does not exist in an object.
---

* content
{:toc}

JavaScript Data Types: Undefined

In JavaScript, "undefined" is a primitive data type that represents a value that is not defined. It is used when a variable is declared but not initialized, or when a property does not exist in an object.

Declaring a variable without assigning a value to it will automatically set its value to "undefined":

```js
let x;
console.log(x); // Output: undefined
```

In the above example, the variable "x" is declared but not assigned a value. Therefore, its value is "undefined".

Undefined is also returned when trying to access a non-existent property of an object:

```js
const obj = { name: "John" };
console.log(obj.age); // Output: undefined
```

In this example, the "age" property does not exist in the "obj" object. Therefore, trying to access it will return "undefined".

It is important to note that "undefined" is a falsy value, meaning it is considered false in boolean expressions:

```js
let x;
if (x) {
  console.log("This will not be executed.");
} else {
  console.log("This will be executed.");
}
```

In the above example, the "if" statement checks the truthiness of "x", which is undefined. Therefore, the "else" block will be executed and "This will be executed." will be logged to the console.

In addition, the "typeof" operator can be used to determine if a variable is undefined:

```js
let x;
console.log(typeof x); // Output: undefined
```

In conclusion, "undefined" is a primitive data type in JavaScript that represents a value that is not defined. It is automatically assigned to variables that are declared but not initialized, or to properties that do not exist in an object. It is considered false in boolean expressions and can be checked using the "typeof" operator.



