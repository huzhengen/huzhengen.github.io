---
layout: post
title:  "Understanding JavaScript Objects"
date:   2023-04-17 13:21:23
categories: javascript
excerpt: Understanding JavaScript Objects
---

* content
{:toc}

Understanding JavaScript Objects

JavaScript is an object-oriented programming language, which means that objects are at the core of the language. In this article, we'll take a closer look at JavaScript objects, including how to create and manipulate them.

Creating Objects in JavaScript

In JavaScript, objects are created using object literals, which are enclosed in curly braces {}. For example, to create a new object representing a person with a name and age, you would use the following code:

```js
var person = {
  name: "John",
  age: 30
};
```

This creates a new object named "person", which has two properties: "name" and "age". The "name" property is set to "John", and the "age" property is set to 30.

Accessing Object Properties

Once you've created an object, you can access its properties using dot notation or bracket notation. For example, to access the "name" property of the "person" object created above, you would use the following code:

```js
var name = person.name;
```

This assigns the value of the "name" property of the "person" object (which is "John") to a variable named "name".

You can also use bracket notation to access object properties, like this:

```js
var name = person["name"];
```

This is equivalent to using dot notation, but allows you to access properties with spaces or other special characters in their names.

Modifying Object Properties

You can modify object properties by assigning new values to them, like this:

```js
person.age = 35;
```

This changes the value of the "age" property of the "person" object to 35.

You can also add new properties to an object by assigning values to them, like this:

```js
person.email = "john@example.com";
```

This adds a new property named "email" to the "person" object, with the value "john@example.com".

Working with Object Methods

In addition to properties, objects can also have methods, which are functions that are attached to the object. For example, to add a method named "greet" to the "person" object created above, you would use the following code:

```js
person.greet = function() {
  console.log("Hello, my name is " + this.name);
};
```

This adds a new method named "greet" to the "person" object, which logs a greeting message to the console using the "name" property of the object.

You can then call the "greet" method of the "person" object like this:

```js
person.greet();
```

This calls the "greet" method of the "person" object, which logs the greeting message to the console.

Conclusion

JavaScript objects are a fundamental part of the language, allowing you to represent data and behavior in a structured and flexible way. By understanding how to create and manipulate objects, and how to work with object properties and methods, you'll be well on your way to mastering the object-oriented features of JavaScript.
