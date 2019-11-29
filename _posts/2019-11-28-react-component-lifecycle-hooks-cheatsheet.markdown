---
layout: post
title: React Component Lifecycle Hooks Cheatsheet 📄
date: 2019-11-28 00:00:00 +0300
description: React Component Lifecycle Hooks Cheatsheet 📄
img: react-component-lifecycle-hooks-cheatsheet.jpeg
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

`useState`, `useEffect`, `useRef` and `memo` are the hooks and the higher order component that allow you to replace React class component lifecycle methods.

## useState

* <strong>Use:</strong> to manage a component's local state.
* <strong>Purpose:</strong> to replace the need for `this.state` and `constructor`.

## useEffect

* <strong>Use:</strong> to manage side effects (Ex. an API request, tracking analytics, interacting with DOM not contained inside your React app, etc).
* <strong>Purpose:</strong> to replace the need for lifecycle methods (<a href="https://dev.to/bunlong/react-component-lifecycle-methods-cheatsheet-1eaf">React Component Lifecycle Methods Cheatsheet</a>).

## useRef

* <strong>Use:</strong> to provide the way to access DOM nodes or HTML elements created in the render method.
* <strong>Purpose:</strong> to helps the `useEffect` to replaces the need for `componentDidUpdate`.

## memo

* <strong>Use:</strong> to manage a component's re-rendering.
* <strong>Purpose:</strong> to replace the need for `shouldComponentUpdate`.

## Explanation with Words and Code

```javascript
const {useEffect, useState, useRef, memo} = React;

const ReactLifecycleHooks = (props) => {

  // Commonly Used Hooks
  // Purpose: Initialize state, read and update state variable.

  // The useState hook allows you to read and update a state variable.
  // The usetState function returns an array containing the current value and the function to 
  // update the value.        
  const [desc, setDesc] = useState('user');
  const [prevCount, setPrevCount] = useState(null);

  // The mounted variable of useRef here is used to check the component is rendered.
  const mounted = useRef();

  console.log('render');

  // The useEffect hook takes 2 arguments, a function containing a side effect action and an array.
  // The array contains the variable(s) that you want to track.
  // When a value in the array changes, the side effect function is executed.

  // The empty array is passed to useEffect as its second argument
  // in the purpose of replacing the useEffect with componentDidMount & componentWillUnmount.
  useEffect(() => {
    console.log('componentDidMount');
    // Lifecycle: Mount immediately after render.
    // Purpose: Initialize state that requires DOM nodes, Network requests and side effects.
    return () => {
      console.log('componentWillUnmount');
      // Lifecycle: Unmount.
      // Purpost: Clean up things such as event handlers, cancel network request, etc.
    }
  }, []);

  // The array containing props.count is passed to useEffect as its second argument
  // in the purpose of replacing the useEffect with componentDidUpdate.
  // The useEffect is tracking the value of props.count, and when it sees a change, the side effect
  // function is executed.
  // When the side effect function executes, the logic of checking componentDidUpdate is executed.
  useEffect(() => {
    if (!mounted.current) {
      mounted.current = true;
    } else {
      console.log('componentDidUpdate');
      // Lifecycle: Update immediately after render.
      // Purpose: Operate on updated DOM or handle network requests.
    }
  }, [props.count]);

  // The logic of calling function getDerivedStateFromProps.
  if (prevCount !== props.count) {
    setDesc(ReactLifecycleHooksOptimization.getDerivedStateFromProps(props, desc));
    setPrevCount(props.count);
  }

  // Required
  // Code to display the component.
  return (
    <>
      {props.count} {desc}
    </>
  )
}

// Return true if you don't want it to rerender, return false if you want it to render.
const shouldComponentUpdate = (prevProps, nextProps) => {
  console.log('shouldComponentUpdate');
  // Lifecycle: Update immediately before render.
  // Purpose: Allows developer to prevent rendering.
  return nextProps.count === prevProps.count;
};

// The memo higher order component allows you to replace the need for shouldComponentUpdate.
// The memo higher order component takes 2 arguments, a component and a comparison function of 
// prevProps and nextProps.
const ReactLifecycleHooksOptimization = memo(ReactLifecycleHooks, shouldComponentUpdate);

// Rarely Used Lifecycle

// The getDerivedStateFromProps function here is created for the purpose of 
// using getDerivedStateFromProps in hooks.
ReactLifecycleHooksOptimization.getDerivedStateFromProps = (nextProps, prevState) => {
  console.log(`getDerivedStateFromProps
  nextProps.count=${nextProps.count}
  prevState=${prevState}`);
  // Lifecycle: Mount and update immediately before render.
  // Purpose: When your state depends on props (should be avoided).
  if (nextProps.count === 0 || nextProps.count > 1) {
    return 'users';
  }
  return 'user';
}

const Nothing = () => 'Nothing';
const App = () => {
  const [component, setComponent] = useState(1);
  const [count, setCount] = useState(1);
  const Component = component > 0 ? ReactLifecycleHooksOptimization : Nothing;  
  return (
    <>
      <button onClick={() => (console.clear(), setComponent(component > 0 ? 0 : 1))}>Mount/Unmount</button>
      <button onClick={() => (console.clear(), setCount(count + 1))}>Update value</button>
      <Component count={count} />
    </>
  );
};

ReactDOM.render(<App />, document.getElementById('app'));
```

Live demo is available on <a href="https://codepen.io/Bunlong/pen/zYYXpZK">CodePen</a>.

## Note

According to the React docs, `getSnapshotBeforeUpdate`, `componentDidCatch` and `getDerivedStateFromError`, there are no Hook equivalents for these methods yet.

## References

* <a href="https://reactjs.org/docs/hooks-intro.html">Hooks at a Glance – React</a>

Thanks for reading ❤ <br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>

## Like ❤️

![React Component Lifecycle Hooks Cheatsheet]({{site.baseurl}}/assets/img/react-component-lifecycle-hooks-cheatsheet.png)
