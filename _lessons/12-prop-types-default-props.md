---
layout: lesson
title: PropTypes and DefaultProps
slug: prop-types-default-props
references:
  - title: 'List of PropTypes'
    url: 'https://facebook.github.io/react/docs/typechecking-with-proptypes.html#react.proptypes'
  - title: 'Default Props'
    url: 'https://facebook.github.io/react/docs/typechecking-with-proptypes.html#default-prop-values'
---

## Prop Types

During development React can do type checking for _props_ components are receiving.

The propTypes typechecking happens after defaultProps are resolved,
so typechecking will also apply to the defaultProps.

```jsx
import React from 'react';

class Lesson extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div className="">
        <h2>{this.props.title}</h2>
        <p>{this.props.description}</p>
        <button onClick={ this.props.action }>{ this.props.actionText }</button>
      </div>
    );
  }
}

Lesson.propTypes = {
  title: React.PropTypes.string.isRequired,
  description: React.PropTypes.string,
  action: React.PropTypes.func.isRequired,
  actionText: React.PropTypes.string
};
```

After specifying the type of the _prop_ you can add `isRequired` to prevent a component from being instantiated without it.


## Default Props

You can also provide a default value for a _prop_ as a fallback.

```js
Lesson.defaultProps = {
  description: 'There is no description for this lesson.'
}
```
