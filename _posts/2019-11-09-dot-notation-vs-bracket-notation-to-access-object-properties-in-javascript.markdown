---
layout: post
title: Dot Notation Vs Bracket Notation to Access Object Properties in JavaScript
date: 2019-11-09 00:00:00 +0300
description: Dot Notation Vs Bracket Notation to Access Object Properties in JavaScript
img: dot-notation-vs-bracket-notation-to-access-object-properties-in-javascript.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

## Accessing Object Properties

There are 2 ways to access object properties are Dot and Bracket in JavaScript.

```javascript
const obj = {
  name: 'value'
};
// Dot Notation
obj.name; // 'value'
// Bracket Notation
obj['name']; // 'value'
```

But the question is always which one should I use 🤔. Let’s get to understand Dot Notation’s issues which is the root to answer the question.

## Dot Notation’s Issues

1. Issue working with invalid Identifiers
2. Issue working with Variables

### 1. Issue working with invalid Identifiers

Dot notations is only work with valid identifiers. But what is identifiers?

> Identifiers are names. In JavaScript, identifiers are used to name variables (and keywords, and functions, and labels).

In JavaScript, the identifier has the following rules:

* case sensitive
* can contain Unicode letters
* $, _, and digits (0–9) are allowed but may not start with a digit

Let’s take a look the examples below and see what happens when we use the Dot notation and Bracket notation.

```javascript
const obj = {
  123: 'digit',
  123name: 'start with digit',
  name123: 'does not start with digit',
  $name: '$ sign',
  name-123: 'hyphen',
  NAME: 'upper case',
  name: 'lower case'
};
```

Using with Dot Notation.

```javascript
obj.123;      // ❌ SyntaxError
obj.123name;  // ❌ SyntaxError
obj.name123;  // ✅ 'does not start with digit'
obj.$name;    // ✅  '$ sign'
obj.name-123;  // ❌ SyntaxError
obj.'name-123';// ❌ SyntaxError
obj.NAME; // ✅ 'upper case'
obj.name; // ✅ 'lower case'
```

Using with Bracket Notation.

```javascript
obj['123'];     // ✅ 'digit'
obj['123name']; // ✅ 'start with digit'
obj['name123']; // ✅ 'does not start with digit'
obj['$name'];   // ✅ '$ sign'
obj['name-123']; // ✅ 'does not start with digit'
obj['NAME']; // ✅ 'upper case'
obj['name']; // ✅ 'lower case'
```

> If you think you have an invalid JavaScript identifier as your property key, use the Bracket Notation.

### 2. Issue working with Variables

Another issue of the Dot notation is working with variables.

Let’s take a look the examples below and see what happens when we use the Dot notation and Bracket notation.

```javascript
const variable = 'name';
const obj = {
  name: 'value'
};
// Dot Notation
obj.variable; // undefined
// Bracket Notation
obj[variable]; // ✅ 'value'
```

> Never use the Dot Notation when using a Variable.

## Undefined Property (Bonus)

When you try to access a property that doesn’t exist, it will return undefined.

```javascript
const emptyObj = {};

emptyObj.name; // undefined

emptyObj['name']; // undefined
```

## Summary

> Use the Dot Notation. Anyway if you’re dealing with invalid identifier or variables, use the Bracket Notation instead.

Thanks for reading ❤ <br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>

