---
layout: post
title: Style Console Output in JavaScript
date: 2019-11-18 00:00:00 +0300
description: Style Console Output in JavaScript
img: style-console-output-in-javascript.png
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

When writing a complex web application one of the important debugging tools is using the logging facility the environment provides. This can help the developer see what's going in the application without interfering with the real UI.

The standard way to print out a message to the JavaScript console of the web browser (or Node application) is using the `log` method of the `console` object. It accepts a list of strings and objects and prints them to the console.

Actually, the `console` object has several additional methods that can be used to fine-tune the logging. There are `debug`, `info`, `log`, `warn`, `error`.

You can use the `%c` directive to apply a CSS style to console output, it help you easily identify debug information in the console.

## Browser's Debugging Console

### 1. Basic Text Styles

```javascript
// Single Text Styles
console.log('This is %cmy stylish message.', 'color: yellow; background-color: blue;');

// Multiple Text Styles
console.log('This is %cmy stylish message. %cAwesome!', 'color: yellow; background-color: blue;', 'color: blue; background-color: yellow;');
```

The text before the `%c` directive will not be affected, but the text after the `%c` directive will be styled using the CSS declarations in the parameter.

### 2. Refactor Text Styles

You can clean up the text using `%s` string substitutions.

```javascript
const styles = 'color: yellow; background-color: blue;';
const text = 'This is my stylish message.';
console.log('%c%s', styles, text);
```

You can clean up the styles by passing the styles as an array and then use the `join()` method to turn the array elements into a string.

```javascript
const styles = [
  'color: yellow',
  'background-color: blue',
].join(';');
const text = 'This is my stylish message.';
console.log('%c%s', styles, text);
```

## Node Debugging Console

You can print the colorful text in Node application as well.

```javascript
console.log('\x1b[33m%s\x1b[0m', 'This is my stylish message.');
```

<a href="https://stackoverflow.com/questions/9781218/how-to-change-node-jss-console-font-color">Color Reference on Stack Overflow.</a>

## References

* <a href="https://developer.mozilla.org/en-US/docs/Web/API/console">MDN Web Docs - Console</a>
* <a href="https://stackoverflow.com/questions/9781218/how-to-change-node-jss-console-font-color">Stack Overflow: Color Reference</a>

Thanks for reading ❤ <br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>

## Like ❤️

![Style Console Output in JavaScript]({{site.baseurl}}/assets/img/style-console-output-in-javascript.png)
