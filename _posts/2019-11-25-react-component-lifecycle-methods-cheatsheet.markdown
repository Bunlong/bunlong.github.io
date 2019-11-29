---
layout: post
title: React Component Lifecycle Methods Cheatsheet 📄
date: 2019-11-25 00:00:00 +0300
description: React Component Lifecycle Methods Cheatsheet 📄
img: react-component-lifecycle-methods-cheatsheet.jpeg
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

<br/>

<table>
  <tr>
    <th>React Component Lifecycle Cheatsheet</th>
  </tr>
  <tr>
    <td><a href="/react-component-lifecycle-methods-cheatsheet">React Component Lifecycle Methods Cheatsheet</a></td>
  </tr>
  <tr>
    <td><a href="/react-component-lifecycle-hooks-cheatsheet">React Component Lifecycle Hooks Cheatsheet</a></td>
  </tr>
</table>

<br/>

Each component in React has a lifecycle which you can monitor and manipulate.

Lifecycle Explanation:

* <strong>Mounting:</strong> Called before your component is displayed on the UI.
* <strong>Updating:</strong> Caused by a change to props or state and rerendered the UI.
* <strong>Unmounting:</strong> Called when your UI will no longer display the component.

## Mounting

### constructor

* <strong>Lifecycle:</strong> Mount immediately before render.
* <strong>Purpose:</strong> Initialize state.

```javascript
// Commonly Used Lifecycle Methods
constructor() {

}
```

### componentDidMount

* <strong>Lifecycle:</strong> Mount immediately after render.
* <strong>Purpose:</strong> Initialize state that requires DOM nodes, Network requests and side effects.

```javascript
componentDidMount() {

}
```

## Updating

### shouldComponentUpdate

* <strong>Lifecycle:</strong> Update immediately before render.
* <strong>Purpose:</strong> Allows developer to prevent rendering.

```javascript
shouldComponentUpdate(nextProps, nextState) { // Optional Parameters

}
```

### render

Code to display the component.

```javascript
// Required
render() {

}
```

### getSnapshotBeforeUpdate

* <strong>Lifecycle:</strong> Update immediately before render output is committed to DOM.
* <strong>Purpose:</strong> Capture DOM information such as scroll position which could change.

```javascript
getSnapshotBeforeUpdate(prevProps, prevState) { // Optional Parameters

}
```

### componentDidUpdate

* <strong>Lifecycle:</strong> Update immediately after render.
* <strong>Purpose:</strong> Operate on updated DOM or handle network requests.

```javascript
componentDidUpdate(prevProps, prevState, snapshot) { // Optional Parameters

}
```

## Mounting & Updating

### getDerivedStateFromProps

* <strong>Lifecycle:</strong> Mount and update immediately before render.
* <strong>Purpose:</strong> When your state depends on props (should be avoided).

```javascript
// Rarely Used Lifecycle Methods
static getDerivedStateFromProps(props, state) { // Optional Parameters

}
```

## Unmounting

### componentWillUnmount

* <strong>Lifecycle:</strong> Unmount.
* <strong>Purpose:</strong> Clean up things such as event handlers, cancel network request, etc.

```javascript
componentWillUnmount() {

}
```

## Other Methods

### componentDidCatch

Creates an error boundary to captures errors from child components.

```javascript
// Special Use Cases
componentDidCatch(error, info) { // Optional Parameters

}
```

## References

* <a href="https://reactjs.org/docs/react-component.html">React.Component – React</a>

Thanks for reading ❤ <br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>

## Like ❤️

![React Component Lifecycle Methods Cheatsheet]({{site.baseurl}}/assets/img/react-component-lifecycle-methods-cheatsheet.jpeg)
