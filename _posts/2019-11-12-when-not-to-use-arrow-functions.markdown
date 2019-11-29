---
layout: post
title: When Not to use Arrow Functions
date: 2019-11-09 00:00:00 +0300
description: When Not to use Arrow Functions
img: when-not-to-use-arrow-functions.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

<!-- ![When Not to use Arrow Functions]({{site.baseurl}}/assets/img/when-not-to-use-arrow-functions.jpg) -->

Here are some instances where you probably should avoid using arrow functions:

## 1. Object Methods

```javascript
const person = {
  points: 23,
  score: () => {
    console.log(this); // 'this' here is window
    this.points++; // 'this' here is window, not person
  }
}
person.score();
console.log(person.points); // 23
```

When you do `console.log(person.points)` the result should be 24 but it’s still 23.

Why? because `this` is always scoped to the parent which is the `window` in this case (it’s not bound to anything else).

You must use regular function instead.

```javascript
const person = {
  points: 23,
  score: function()  {
    this.points++; // 'this' here is person
  }
}
person.score();
console.log(person.points); // 24
```

## 2. Callback Functions with Dynamic Context

```javascript
const button = document.getElementById('myButton');
button.addEventListener('click', () => {
  console.log(this); // 'this' here is window
  this.innerHTML = 'Clicked Button'; // 'this' here is window, not button
});
```

When you click on `myButton` it won’t actually work.

Why? because `this` is not bound to the button, but instead bound to its parent scope which is the `window` in this case.

You must use regular function instead:

```javascript
const button = document.getElementById('myButton');
button.addEventListener('click', function() {
  console.log(this); // button
  this.innerHTML = 'Clicked Button'; // 'this' here is button
});
```

## 3. Prototype Methods

```javascript
class Person {
  constructor(points) {
    this.points = points;
  }
}
Person.prototype.info = () => {
  console.log(this); // 'this' here is window
  return `Points: ${this.points}`; // // 'this' here is window, not Person
};
const me = new Person(24);
console.log(me.info());
```

When you do `console.log(me.info())` it won’t actually work.

Why? Why? because `this` is not bound to the Person, but instead bound to its parent scope which is the `window` in this case.

You must use regular function instead:

```javascript
class Person {
  constructor(points) {
    this.points = points;
  }
}
Person.prototype.info = function() {
  console.log(this); // Person
  return `Points: ${this.points}`; // // 'this' here is Person
};
const me = new Person(24);
console.log(me.info());
```

## 4. arguments Object

```javascript
const logArgument = () => {
  console.log(arguments[0]);
};
logArgument('Hi!'); // ReferenceError: arguments is not defined
```

It won’t actually work.

Why? because arrow functions do not automatically bind their own `arguments` value, and that there was no reference to `arguments` in logArgument’s outer scope, so the compiler throws a reference error.

You must use regular function instead:

```javascript
const logArgument = function () {
  console.log(arguments[0]);
};
logArgument('Hi!'); // Hi!
```

## Summary

Arrow functions are terrific, but not suitable for all situations. Places where they will not only help, but cause you trouble.

> Arrow functions doesn’t replace regular functions.

Thanks for reading ❤ <br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>
