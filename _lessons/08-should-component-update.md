---
layout: lesson
title: shouldComponentUpdate
slug: should-component-update
references:
  - title: 'shouldComponentUpdate from React official site'
    url: 'https://facebook.github.io/react/docs/optimizing-performance.html#shouldcomponentupdate-in-action'
---

Knowing how our components behave might also unveil when they actually need to be rendered again.

Given this loading bar component, it’s noticeable that unless its hidden state changes after being mounted, we won’t need to update it.

```jsx
class LoadingBar extends React.Component {
  render() {
    return (
      <div className='loading-bar' hidden={ this.props.hidden }>
        <div className='loading-bar-progress'></div>
      </div>
    );
  }
}
```

To make our component update cycle smarter we can use `shouldComponentUpdate` and compare the upcoming _props_ and _state_ from the current one.

```jsx
class LoadingBar extends React.Component {
  shouldComponentUpdate(nextProps, nextStates) {
    return this.props.hidden !== nextProps.hidden;
  }
  render() {
    return (
      <div className='loading-bar' hidden={ this.props.hidden }>
        <div className='loading-bar-progress'></div>
      </div>
    );
  }
}
```

With a simple and straight forward line of code our component gets smarter.

## No updates at all

If the component doesn’t contain any dynamic data we can just return `false` inside `shouldComponentUpdate` and it will only get rendered once.
