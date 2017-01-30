---
layout: lesson
title: State
slug: state
references:
  - title: 'Using State Correctly'
    url: 'https://facebook.github.io/react/docs/state-and-lifecycle.html#using-state-correctly'
  - title: 'Lifting State Up'
    url: 'https://facebook.github.io/react/docs/lifting-state-up.html'
  - title: 'Using a function in setState instead of an object'
    url: 'https://medium.com/@shopsifter/using-a-function-in-setstate-instead-of-an-object-1f5cfd6e55d1#.dd532hyfa'
---

The states are used to reflect a mutation in a component triggered by itself like internal flags or fetched data.

We set the initial states in the constructor of the component like this:

```jsx
class NameForm extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      name: ''
    };
  }

  handleChange(e) {
    this.setState({ name: e.target.value });
  }

  render() {
    return (
      <form action="?">
        <h3>Welcome { this.state.name }</h3>
        <input onChange={ this.handleChange.bind(this) }/>
        <button type="submit">Continue</button>
      </form>
    );
  }
}
```

Notice that instead of modifying `this.state`, we used `this.setState` method and pass down one or more states we want to change in an object. The only place where you can assign `this.state` is the constructor.

Also, _state updates are asynchronous_. That's why in some cases is recommended to change states passing down a function.

```js
this.setState((prevState, props) => ({ count: prevState.count + 1 }));
```
