---
layout: post
title: Single-Quotes Vs Double-Quotes in JavaScript
date: 2019-11-21 00:00:00 +0300
description: Single-Quotes Vs Double-Quotes in JavaScript
img: single-quotes-vs-double-quotes-in-javascript.png
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

JavaScript, allows you to use either single quotes (`''`) or double quotes (`""`) to create a string literals.

## Both Have the Same Qualities

They are essentially the same.

```javascript
console.log('abc' === "abc"); // true
```

A single quoted string can have double quotes within it without having to escape them.

```javascript
console.log('Single quotes with a double ( " ) quote in the middle.');
```

A double quoted string can have single quotes without escaping them.

```javascript
console.log("Double quotes with a single ( ' ) quote in the middle.");
```

Each type must escape their own type.

```javascript
console.log('single quotes ( \' ) must escape a single quote');

console.log("double quotes ( \" ) must escape a double quote");
```

## Pros of Using Single Quotes

One popular argument for single quotes is when you have to write html within JavaScript.

If you use single quotes you can write as following.

```javascript
const html = '<div id="some_div"></div>';
```

If you use double quotes you must escape each nested `"`

```javascript
const html = "<div id=\"some_div\"></div>";
```

which can get annoying or you could use single quotes within the html string.

## Pros of Using Double Quotes

Remember that JSON only allows double quotes.

```javascript
{
  "in_json": "You use only double quotes."
}
```

## Single Quotes are More Common

A few repositories of popular JavaScript projects reveals that single quotes are favored over double quotes.

```
+------------+----------------------------------+
| Projects   | Dominant of Single Quotes        |
+------------+----------------------------------+
| async      | Single-Quotes ('') 76% of quotes |
| express    | Single-Quotes ('') 92% of quotes |
| lodash     | Single-Quotes ('') 73% of quotes |
| request    | Single-Quotes ('') 97% of quotes |
| underscore | Single-Quotes ('') 78% of quotes |
| angular    | Single-Quotes ('') 58% of quotes |
| react      | Single-Quotes ('') 52% of quotes |
+------------+----------------------------------+
```

You can see that front-end libraries (React, Angualar, ...) have more double quotes than the other libraries as might have to do with the presence of HTML fragments.

Let's take a look at a few style guides you can see that about half recommend single quotes and other half double quotes.

* <a href="https://developers.google.com/closure/utilities">gjslint</a> (Google Closure Linter) favors single quotes (`''`).
* <a href="https://www.npmjs.com/package/standard">standard</a> (an NPM package) favors single quotes (`''`).
* <a href="http://www.jslint.com/">jslint</a> favors double quotes (`""`).
* <a href="https://eslint.org/">eslint</a> favors double quotes (`""`).
* <a href="https://github.com/Microsoft/TypeScript/wiki/Coding-guidelines">TypeScript Contributors Coding Guidelines</a> favors double quotes (`""`).

## Summary

You should define one standard style and stick with it. I recommend single quotes (`''`) as a solid standard and more common.

In ES6, there is another option to create a string literals using <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals">Template literals</a>.

## References

* <a href="https://stackoverflow.com/questions/242813/when-to-use-double-or-single-quotes-in-javascript">Stack Overflow: When to Use Double or Single Quotes in JavaScript?</a>
* <a href="https://stackoverflow.com/questions/9959928/double-quotes-vs-single-quotes-in-javascript">Stack Overflow: Double Quotes Vs Single Quotes in JavaScript</a>
* <a href="https://stackoverflow.com/questions/3149192/difference-between-single-quotes-and-double-quotes-in-javascript">Stack Overflow: Difference Between Single Quotes and Double Quotes in Javascript</a>

Thanks for reading ❤ <br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>

## Like ❤️

!['Single-Quotes' Vs "Double-Quotes" in JavaScript]({{site.baseurl}}/assets/img/single-quotes-vs-double-quotes-in-javascript.png)
