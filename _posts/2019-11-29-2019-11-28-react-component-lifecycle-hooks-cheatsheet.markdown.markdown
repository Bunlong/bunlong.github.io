---
layout: post
title: React Child Component Cheatsheet 📄
date: 2019-11-29 00:00:00 +0300
description: React Child Component Cheatsheet 📄
img: react-child-component-cheatsheet.png
fig-caption: # Add figcaption (optional)
tags: [javascript, webdev, beginners, codenewbie] # add tag
---

<hr/>

## Table of Contents
  * [1. Nested Components](#nested-components)
  * [2. Child Components](#child-components)
    * [2.1. Everything Can be a Child Component](#everything-can-be-a-child-component)
    * [2.2. Function as a Child Component](#function-as-a-child-component)
  * [3. Manipulating Children Components](#manipulating-children-component)
    * [3.1. Looping Children Components](#looping-children-components)
    * [3.2. Counting Children Components](#counting-children-components)
    * [3.3. Converting Children Components to an Array](#converting-children-components-to-an-array)
    * [3.4. Enforcing Only One Child Component](#enforcing-only-one-child-component)
  * [4. Modifying Children Components](#modifying-children-components)
    * [4.1. Modifying Children Props](#modifying-children-props)
    * [4.1. Cloning Elements](#cloning-elements)

<hr/>

<a name="nested-components"></a>
## 1. Nested Components

Nested Components is children nested inside parent components. It simply help us create more complex UI structures.

For instance, a pseudo of nested html tags.

```html
<html>
  <toolbar></toolbar>
  <content>
    <table></table>
  </content>
</html>
```

<a name="child-components"></a>
## 2. Child Components

For instance, we have two `<Item />` components nested inside a `<List />` component.

![Child Components]({{site.baseurl}}/assets/img/child-components.png)

```javascript
<List>
  <Item />
  <Item />
</List>
```

We can use `props.children` to access the nested children components of a parent component.

```javascript
Class List extends React.Component {
  render() {
    return <>{this.props.childrent}</>;
  }
}
```

Live demo is available on <a href="https://codepen.io/Bunlong/pen/NzZbZv">CodePen</a>.

<a name="everything-can-be-a-child-component"></a>
### 2.1. Everything Can be a Child Component

In React, children don't have to be components, they can be anything.

For instance, we can pass `<List />` component some text as child.

```javascript
<List>Hello World!</List>
```

<a name="function-as-a-child-component"></a>
### 2.2. Function as a Child Component

We can pass a render function to a component as the children prop.

```javascript
<Executor>
  {(msg) => <p>Hello {msg}!</p>}
</Executor>
```

And the `Executor` component will look something like this.

```javascript
class Executor extends React.Component {
  render() {
    return this.props.children('World');
  }
}
```

Live demo is available on <a href="https://codepen.io/Bunlong/pen/jKjmbr">CodePen</a>.

<a name="manipulating-children-component"></a>
## 3. Manipulating Children Components

`props.children` can be any type, such as array, function, object, etc.

React provides a bunch of utilities to manipulate any type of `props.children` as following.

<a name="looping-children-components"></a>
### 3.1. Looping Children Components

React provides two utilities `React.Children.map` and `React.Children.forEach` to loop over children components.

<strong>React.Children.map</strong>

Return: a child, null, or undefined.

![React.Children.map]({{site.baseurl}}/assets/img/react-children-map-1.png)

```javascript
class IgnoreSecondChild extends React.Component {
  render() {
    const children = this.props.children;
    return (
      <div>
        {React.Children.map(children, (child, index) => {
          if (index == 1) return; // Ignore the second child
          return child;
        })}
      </div>
    );
  }
}
```

`<IgnoreSecondChild />` components maps over all its children but ignoring the second child and returning all others.

```javascript
<IgnoreSecondChild>
  <h1>Child1</h1>
  <h1>Child2</h1> { /* Ignore the second child */ }
</IgnoreSecondChild>
```

![React.Children.map]({{site.baseurl}}/assets/img/react-children-map-2.png)

Live demo is available on <a href="https://codepen.io/Bunlong/pen/yEdXGr">CodePen</a>.

<a name="counting-children-components"></a>
### 3.2. Counting Children Components

React provides `React.Children.count` utilities to count any type of children.

```javascript
class ChildrenCounter extends React.Component {
  render() {
    return <p>React.Children.count(this.props.children)</p>;
  }
}
```

It would returns the number of children no matter what type they are.

```javascript
<ChildrenCounter>
  Hello World!
</ChildrenCounter>
```

Live demo is available on <a href="https://codepen.io/Bunlong/pen/yEmYbE">CodePen</a>.

<a name="converting-children-components-to-an-array"></a>
### 3.3. Converting Children Components to an Array

React provides `React.Children.toArray` utilities to convert the children to an array. This would be useful if you needed to sort the children component.

```javascript
class ChildrenSorter extends React.Component {
  render() {
    const child = React.Children.toArray(this.props.children);
    return <p>{child.sort().join(' ')}</p>;
  }
}
```

It would render the sorted strings.

```javascript
<ChildrenSorter>
  {'map'}{'forEach'}{'count'}{'toArray'}
</ChildrenSorter>
```

Live demo is available on <a href="https://codepen.io/Bunlong/pen/wXLqWQ">CodePen</a>.

<a name="enforcing-only-one-child-component"></a>
### 3.4. Enforcing Only One Child Component

React provides `React.Children.only` utilities to verifies that children has only one child (a React element) and returns it. Otherwise this method throws an error.

```javascript
class Executor extends React.Component {
  render() {
    return React.Children.only(this.props.children());
  }
}
```

Live demo is available on <a href="https://codepen.io/Bunlong/pen/XYLagK">CodePen</a>.

<a name="modifying-children-components"></a>
## 4. Modifying Children Components

For instance, we have a `<RadioGroup />` component which contain many `<RadioButton />` components (in raw html `<input type="radio"> inside a <label>`).

```javascript
render() {
  <RadioGroup>
    <RadioButton value="1">1</RadioButton>
    <RadioButton value="2">2</RadioButton>
    <RadioButton value="3">2</RadioButton>
  </RadioGroup>
}
```

![Modifying Children Components]({{site.baseurl}}/assets/img/modifying-children-components.png)

The inputs are not grouped as they don't have the same name attributes.

We can modify and assign a name property to every single `<RadioButton />` components as following.

```javascript
render() {
  <RadioGroup>
    <RadioButton name="rate" value="1">1</RadioButton>
    <RadioButton name="rate" value="2">2</RadioButton>
    <RadioButton name="rate" value="3">2</RadioButton>
  </RadioGroup>
}
```

But what we want is to pass the `<RadioGroup />` components a unique name and its child will get and have its name automatically.

<a name="modifying-children-props"></a>
### 4.1. Modifying Children Props

In `<RadioGroup />` components we will add a new method called renderChildwhere we will modify the children props.

```javascript
class RadioGroup extends React.Component {

  renderChildren() {
    // TODo: Change the name prop of all children
    // to this.props.name
    return this.props.children; 
  }

  render() {
    return (
      <div>
        {this.renderChildren()}
      </div>
    )
  }
}
```

We do map loop over the children components to get each individual child in `renderChildren` method.

```javascript
renderChildren() {
  return React.Children.map(this.props.children, child => {
    // TODO: Change the name prop of all children
    // to this.props.name
    return child;
  })
}
```

So far, How can we modify the children properties?

<a name="cloning-elements"></a>
### 4.2. Cloning Elements

React provides `React.cloneElement` utilities to clone and return a new React element.

`React.cloneElement` takes 2 arguments, an element we want to clone and an object of props we want to be set on the cloned element.

For instance

```javascript
const cloned = React.cloneElement(element, {
  name: 'rate'
});
```

The `cloned` element will now have the `name` prop set to "rate".

Get back to `<RadioGroup />` components, we will clone each child and set the name prop of the cloned child to `this.props.name`.

```javascript
renderChildren() {
  return React.Children.map(this.props.children, child => {
    return React.cloneElement(child, {
      name: this.props.name
    })
  })
}
```

Then we pass a unique name to each `<RadioGroup />` components.

```javascript
<RadioGroup name="rate">
  <RadioButton value="first">First</RadioButton>
  <RadioButton value="second">Second</RadioButton>
  <RadioButton value="third">Third</RadioButton>
</RadioGroup>
```

![Cloning Elements]({{site.baseurl}}/assets/img/cloning-elments.png)

Instead of manually having to set the name attribute to each components, we just tell our `<RadioGroup />` what we want to the name to be.

The complete​​​ instance.

```javascript
class RadioGroup extends React.Component {

  renderChildren() {
    return React.Children.map(this.props.children, child => {
      return React.cloneElement(child, {
        name: this.props.name
      });
    })
  }

  render() {
    return (
      <div className="group">
        {this.renderChildren()}
      </div>
    )
  }
}

class RadioButton extends React.Component {
  render() {
    return (
      <label>
        <input type="radio" value={this.props.value} name={this.props.name} />
        {this.props.children}
      </label>
    );
  }
}

ReactDOM.render(
  <RadioGroup name="rate">
    <RadioButton value="first">First</RadioButton>
    <RadioButton value="second">Second</RadioButton>
    <RadioButton value="third">Third</RadioButton>
  </RadioGroup>, 
  document.getElementById('app')
);
```

Live demo is available on <a href="https://codepen.io/Bunlong/pen/aKgVgd">CodePen</a>.

## References

* <a href="https://reactjs.org/docs/react-api.html#reactchildren">React.Children - React</a>
* <a href="https://jaketrent.com/post/send-props-to-children-react/">Send props to Child - React</a>
* <a href="https://mxstbr.com/">MXSTBR (React.Children) - React</a>

Thanks for reading ❤ <br/>
Say Hello! <a href="https://twitter.com/bunlongvan">Twitter</a> | <a href="https://github.com/bunlong">Github</a> | <a href="https://www.linkedin.com/in/bunlongvan">LinkedIn</a> | <a href="https://www.facebook.com/codervlog">Facebook</a> | <a href="https://www.instagram.com/codervlog">Instagram</a>
