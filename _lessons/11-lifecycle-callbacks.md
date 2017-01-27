---
layout: lesson
title: Lifecycle callbacks
slug: lifecycle-callbacks
references:
  - title: 'Adding Lifecycle Methods to a Class'
    url: 'https://facebook.github.io/react/docs/state-and-lifecycle.html#adding-lifecycle-methods-to-a-class'
  - title: 'The Component Lifecycle'
    url: 'https://facebook.github.io/react/docs/react-component.html#the-component-lifecycle'
  - title: 'Understanding the React Component Lifecycle'
    url: 'http://busypeoples.github.io/post/react-component-lifecycle/'
---

For class based components, we have a set of methods available to call during its mounting, unmounting and update cycles.

This is what gets called when a component gets rendered for the first time:

- `constructor()`
- `componentWillMount()`
- `render()`
- `componentDidMount()`

When its state changes or a new prop is passed:

- `componentWillReceiveProps()`
- `shouldComponentUpdate()`
- `componentWillUpdate()`
- `render()`
- `componentDidUpdate()`

Finally, before the component gets remove from the DOM `componentWillUnmount()` is called.
