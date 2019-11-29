---
layout: post
title: Arrow Functions Return Rules in JavaScript
date: 2019-11-15 00:00:00 +0300
description: Arrow Functions Return Rules in JavaScript
img: arrow-functions-return-rules-in-javascript.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

There are 2 ways for returning values in arrow functions:

1. Explicit Return
2. Implicit Return

## 1. Explicit Return

### What is Explicit Return?

A function is returned values using the return keyword, it's called an explicit return.

### The Rules of Explicit Return

You must use an explicit return statement in a block body.

### Example

```javascript
// Single-line
const explicit = (value) => { return value; }

// Multi-line
const explicit = (value) => {
  return value;
}
```

## 2. Implicit Return

### What is Implicit Return?

A function is returned values without using the return keyword, it's called an implicit return.

### The Rules of Implicit Return

You must use an implicit return in a concise body.

### Example

```javascript
// Single-line
const implicit = (value) => value;

// Multi-line
const implicit = (value) => (
  value
);
```

### Issue Returning Objects

When using implicit returns, object literals must be wrapped in parenthesis so that the curly braces are not mistaken for the opening of the function's body.

```javascript
const implicit = () => { value: 1 };
implicit(); // undefined

const implicit = () => ({ value: 1 });
implicit(); // { value: 1 }
```

## Parens Rules

Arrow functions can omit parentheses when they have exactly one parameter.

```javascript
// Arrow Functions, with parentheses
const myFunction = (p) => {}

// Arrow Functions, without parentheses
const myFunction = p => {}
```

In all other cases (multiple parameters), the parameter(s) must be wrapped in parentheses.

```javascript
// Arrow Function, with parentheses
const myFunction = (p1, p2) => {}
```

## References

* <a href="https://jaketrent.com/post/javascript-arrow-function-return-rules">JavaScript Arrow Function Return Rules</a>
* <a href="https://eslint.org/docs/rules/arrow-parens">Eslint - arrow-parens rules</a>
* <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions">MDN Web Docs - Arrow functions</a>

Thanks for reading ❤
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>

## Like ❤️

![Arrow Functions Return Rules in JavaScript]({{site.baseurl}}/assets/img/arrow-functions-return-rules-in-javascript.png)
