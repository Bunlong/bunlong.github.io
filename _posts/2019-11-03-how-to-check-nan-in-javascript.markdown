---
layout: post
title: How to Check NaN in JavaScript
date: 2019-11-03 00:00:00 +0300
description: How to Check NaN in JavaScript # Add post description (optional)
img: how-to-check-nan-in-javascript.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

## What is NaN?

* In JavaScript, NaN is kind of a value (an invalid number).
* NaN stands for “Not a Number”.
* You get NaN when you try to do some mathematical operations on values that are not Numbers.

```javascript
const invalid = 100 / 'string';
console.log(invalid); // NaN
```

## Problem Checking NaN

`isNaN` is a very special value that never equals to itself 😫.

```javascript
const nan = NaN;
console.log(nan === NaN); // false
console.log(nan == NaN); // false
```

Luckily, JavaScript created the global utility `isNaN` to help us check if a value is equal to NaN.

## Problem with isNaN

But there is the problem with `isNaN` as well when using with String type.

```javascript
const nan = NaN;
console.log(isNaN(nan)); // true ✅
const value = 'string';
console.log(isNaN(value)); // true 😱
```

`isNaN` returns true if the argument equals to NaN, and otherwise returns false. And it tries to convert the argument’s type into a Number type.

```javascript
const value = 'string';

console.log(Number(value)); // NaN
```

When you try to convert the String type to a Number type, it returns NaN. That’s why `isNaN('string')` it’s returning true.

## Problem Solved with Number.isNaN

That’s why the `Number.isNaN` method was introduced. It doesn’t try to convert the argument’s type to a Number type.

```javascript
const number = 100;
isNaN(number) // false ✅
Number.isNaN(number) // false ✅
const nan = NaN;
isNaN(nan) // true ✅
Number.isNaN(nan) // true ✅
const value = 'string';
isNaN(value) // true ❌
Number.isNaN(value) // false ✅
```
## Summary

> When checking if a value is equal to NaN. Use the Number.isNaN method. Do NOT use isNaN 🤓

Thanks for reading ❤ 
<br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>
