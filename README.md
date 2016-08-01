# React Initial State

## Objectives

1. Explain how to define a component's initial state
2. Explain the difference between initialState and defaultProps
3. Practice defining a component's initial state

## Overview

Similarly to how we taught props, we want to walk students through the
difference between `getInitialState()` and setting `this.state` in the
constructor.

So for example, we'd have

```javascript
const Toggler = React.createClass({
  getInitialState() {
    return {
      on: false
    }
  },

  render() {
    return (
      <div>
        {React.Children.map(c =>
          React.cloneElement(c, { ...c.props, on: this.state.on }))}
      </div>
    )
  }
})
```

for `createClass()`, and some variation of

```javascript
class Toggler extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      on: false
    }
  }

  render() {
    return (
      <div>
        {React.Children.map(this.props.children, c =>
          React.cloneElement(c, { ...c.props, on: this.state.on }))}
      </div>
    )
  }
}
```

We don't need to cover `setState()` just yet, but it's a good idea to start
mentioning how props and state are different (and how props allows us to be
more declarative and is generally preferable to state).

## Resources

- [React.cloneElement()](https://facebook.github.io/react/docs/top-level-api.html#react.cloneelement)
- [Props in getInitialState Is an Anti-Pattern](https://facebook.github.io/react/tips/props-in-getInitialState-as-anti-pattern.html)
