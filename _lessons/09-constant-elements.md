---
layout: lesson
title: Avoid unnecessary element reconciling
slug: constant-elements
---

Every change on a parent component will trigger a new `React.createElement` call for its children, adding a new reconciling step for each of them as a consequence which makes no sense if we know that our component or part of it will always remain constant.

To mitigate this, declare inner components as a constants.

```jsx
import React from 'react';

const icon = <Icon/>;

class SearchButton extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <button disabled={ this.props.disabled }>
        { icon } Search
      </button>
    );
  }
}
```

You can get similar behaviors by returning false when the component should update or extending from `PureComponent` class as mentioned before, something that might not be possible when component doesn’t belong to your project codebase.
