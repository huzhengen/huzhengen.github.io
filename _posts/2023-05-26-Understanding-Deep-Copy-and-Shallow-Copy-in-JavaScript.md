---
layout: post
title:  "Understanding Deep Copy and Shallow Copy in JavaScript"
date:   2023-05-26 14:35:35 +0800
categories: javascript
excerpt: In JavaScript, copying objects and arrays is a common task. However, it's important to understand the concepts of deep copy and shallow copy to avoid unexpected behavior and maintain data integrity. This article will explore the differences between deep copy and shallow copy in JavaScript and provide examples to clarify their usage.
---

* content
{:toc}

Understanding Deep Copy and Shallow Copy in JavaScript

Introduction:

In JavaScript, copying objects and arrays is a common task. However, it's important to understand the concepts of deep copy and shallow copy to avoid unexpected behavior and maintain data integrity. This article will explore the differences between deep copy and shallow copy in JavaScript and provide examples to clarify their usage.

1. Shallow Copy:

    Shallow copy creates a new object or array but maintains references to the original nested objects. In other words, only the top-level structure is duplicated, while the nested elements are still shared between the original and copied objects.

Example:

```js
// Shallow copy example
const originalArray = [1, 2, 3];
const shallowCopy = originalArray.slice();

originalArray[0] = 'modified';
console.log(originalArray);    // Output: ['modified', 2, 3]
console.log(shallowCopy);      // Output: [1, 2, 3]
```

In the example above, modifying the value of `originalArray[0]` does not affect the shallow copy. However, if the array contains objects or arrays as elements, changes to those nested elements will affect both the original and the shallow copy.

2. Deep Copy:

    Deep copy creates a completely independent copy of an object or array, including all nested objects or arrays. This means that any modifications made to the copied object will not affect the original or vice versa.

Example:

```js
// Deep copy example
const originalObject = { 
  name: 'John',
  age: 25,
  address: {
    city: 'New York',
    country: 'USA'
  }
};

const deepCopy = JSON.parse(JSON.stringify(originalObject));

originalObject.address.city = 'San Francisco';
console.log(originalObject);   // Output: { name: 'John', age: 25, address: { city: 'San Francisco', country: 'USA' } }
console.log(deepCopy);         // Output: { name: 'John', age: 25, address: { city: 'New York', country: 'USA' } }
```

In this example, the deep copy `deepCopy` is created using `JSON.parse(JSON.stringify())`. Any modifications made to the `address.city` property of the original object do not affect the deep copy.

3. Choosing Between Deep Copy and Shallow Copy:

    The choice between deep copy and shallow copy depends on the specific requirements of your program. Shallow copy is usually sufficient for simple data structures, while deep copy is necessary when you need to ensure complete independence between the original and copied objects, especially when dealing with nested objects or arrays.

It's worth noting that deep copying complex objects with circular references or functions cannot be achieved using `JSON.parse(JSON.stringify())`. In such cases, libraries like `lodash` provide deep copy functions that can handle these scenarios.

Conclusion:

Understanding the differences between deep copy and shallow copy is crucial when working with objects and arrays in JavaScript. Shallow copy creates a new object with references to the original nested elements, while deep copy creates an independent copy of the entire data structure. By choosing the appropriate copying technique, you can ensure data integrity and avoid unexpected side effects in your JavaScript code.

Remember to carefully consider your specific use case and the potential implications of copying methods when working with objects and arrays in JavaScript.

I hope this article helps you gain a better understanding of JavaScript's deep copy and shallow copy concepts.
