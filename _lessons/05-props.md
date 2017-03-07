---
layout: lesson
title: Props
slug: props
references:
  - title: 'Components and Props'
    url: 'https://facebook.github.io/react/docs/components-and-props.html'
  - title: 'Children in JSX'
    url: 'https://facebook.github.io/react/docs/jsx-in-depth.html#children-in-jsx'
---

React uses one-way data flow, data can only be passed from the parent component to the child component using _props_.

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

class Welcome extends React.Component {
  render() {
    return <div>Hello, { this.props.name }</div>;
  }
}

ReactDOM.render(
  <Welcome name="Mark" />
  document.getElementById('root')
);
```

The child-parent communication and sibling communication is more complex and not recommended though it can be achieved by passing methods through _props_ and keeping the content pointing to the parent or the sibling.

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

class Button extends React.Component {
  render() {
    return <button onClick={ this.props.handleClick }></button>;
  }
}

class Welcome extends React.Component {
  salute(event) {
    alert(`Hello, ${ this.props.name }`);
  }

  render() {
    return (
      <div>
        <p>Hello, { this.props.name }</p>
        <Button handleClick={ this.salute.bind(this) } />
      </div>);
  }
}

ReactDOM.render(
  <Welcome name="Mark"/>,
  document.getElementById('root')
);
```

Remember to `bind` the method passed to the current component, if you use `this` inside the method.

Note that:

1. _props_ are **read-only**
2. you can [spread attributes](https://facebook.github.io/react/docs/jsx-in-depth.html#spread-attributes)


### The `children` prop

The content between the opening and closing tag of a component is passed as a `prop` called `children`, you can access it through `this.props.children`.
