---
layout: post
title:  "Understanding JavaScript Promises"
date:   2023-04-18 15:21:23
categories: javascript
excerpt: Understanding JavaScript Promises
---

* content
{:toc}

Understanding JavaScript Promises

Promises are a core feature of modern JavaScript, providing a powerful way to handle asynchronous operations and avoid callback hell. In this article, we'll take a closer look at JavaScript promises, including how they work, how to create them, and how to use them effectively.

What are Promises in JavaScript?

A promise is an object that represents a value that may not be available yet, but will be at some point in the future. Promises can be in one of three states:

* Pending: The initial state, representing a promise that hasn't yet been fulfilled or rejected.
* Fulfilled: The state of a promise that has been successfully resolved, with a value available.
* Rejected: The state of a promise that has been unsuccessfully resolved, with an error available.

Promises are designed to handle asynchronous operations, such as fetching data from a server or reading a file from disk. By using promises, you can avoid callback hell and write cleaner, more maintainable code.

Creating Promises in JavaScript

Promises in JavaScript are created using the Promise constructor, which takes a single argument: a function that defines the behavior of the promise. This function takes two arguments: a resolve function and a reject function.

Here's an example of creating a simple promise that resolves with a value after a short delay:

```js
const delay = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

delay(1000)
  .then(() => console.log("Delayed message"));
```

This creates a new promise that resolves after 1 second, and logs a message to the console.

Working with Promises in JavaScript

Once you have a promise, you can work with it using the then method, which takes two functions as arguments: a success function and an error function. These functions are called when the promise is fulfilled or rejected, respectively.

Here's an example of working with a promise that resolves successfully:

```js
const fetchData = () => new Promise((resolve) => {
  // Fetch data from server
  const data = { id: 1, name: "John" };
  
  // Resolve promise with data
  resolve(data);
});

fetchData()
  .then((data) => console.log("Data received", data));
```

This creates a new promise that fetches data from a server, and resolves with the data. The then method is then used to log the received data to the console.

If the promise is rejected, the error function passed to then will be called instead of the success function:

```js
const fetchError = () => new Promise((resolve, reject) => {
  // Fetch data from server
  const error = new Error("Unable to fetch data");
  
  // Reject promise with error
  reject(error);
});

fetchError()
  .then((data) => console.log("Data received", data))
  .catch((error) => console.error("Error fetching data", error));
```

This creates a new promise that fetches data from a server, but intentionally rejects the promise with an error. The catch method is then used to handle the error and log an error message to the console.

Conclusion

Promises are a powerful tool for handling asynchronous operations in modern JavaScript, and are widely used in frameworks and libraries like React and Angular. By understanding how promises work, and how to create and use them effectively, you can write cleaner, more maintainable code and avoid callback hell.
