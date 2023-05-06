---
layout: post
title:  "Object-Oriented Programming in JavaScript"
date:   2023-05-01 13:19:13 +0800
categories: javascript
excerpt: Object-Oriented Programming in JavaScript
---

* content
{:toc}

Object-Oriented Programming in JavaScript

Object-oriented programming (OOP) is a popular programming paradigm that allows us to organize code into reusable and modular components. JavaScript is a flexible language that supports both OOP and functional programming. In this article, we'll explore the basics of OOP in JavaScript.

Classes:

In JavaScript, classes are a way to define blueprints for objects. A class is a template that defines the properties and methods of an object. To create a class, we use the "class" keyword followed by the class name. Here's an example:

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  sayHello() {
    console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
  }
}
```

In this example, we've created a class called "Person" that has two properties (name and age) and one method (sayHello). The constructor method is used to initialize the object's properties.

To create an instance of a class, we use the "new" keyword followed by the class name:

```js
const person1 = new Person("John", 30);
const person2 = new Person("Jane", 25);

person1.sayHello(); // Output: "Hello, my name is John and I am 30 years old."
person2.sayHello(); // Output: "Hello, my name is Jane and I am 25 years old."
```

Inheritance:

Inheritance allows us to create a new class based on an existing class. The new class inherits the properties and methods of the existing class and can also add its own properties and methods. To create a subclass, we use the "extends" keyword followed by the name of the parent class. Here's an example:

```js
class Student extends Person {
  constructor(name, age, major) {
    super(name, age);
    this.major = major;
  }
  
  sayMajor() {
    console.log(`My major is ${this.major}.`);
  }
}

const student1 = new Student("Bob", 20, "Computer Science");
student1.sayHello(); // Output: "Hello, my name is Bob and I am 20 years old."
student1.sayMajor(); // Output: "My major is Computer Science."
```

In this example, we've created a subclass called "Student" that extends the "Person" class. The "super" keyword is used to call the constructor of the parent class and initialize the inherited properties. The "Student" class also has its own property (major) and method (sayMajor).

Conclusion:

Object-oriented programming is a powerful paradigm that allows us to write modular and reusable code. JavaScript's support for classes and inheritance makes it a versatile language for OOP. By mastering these concepts, you can write cleaner and more efficient code in your JavaScript projects.