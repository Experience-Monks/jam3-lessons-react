---
layout: lesson
title: JSX
slug: jsx
references:
- title: 'Introducing JSX'
  url: 'https://facebook.github.io/react/docs/introducing-jsx.html'
- title: 'JSX In Depth'
  url: 'https://facebook.github.io/react/docs/jsx-in-depth.html'
---

First of all, JSX is **neither** a string **nor** HTML but an extension to JavaScript to simplify the nested declaration of React elements.

```jsx
<Welcome size="huge">
  <p>Hey, you!</p>
</Welcome>
```

The JSX definition you find above become this after being transpiled.

```js
import React from 'react';

React.createElement(
  Welcome,
  { size: 'huge' },
  [ React.createElement('p', null, 'Hey, you!') ]
);
```


## Use capitalized names for user-defined components

`React` will interpret elements starting with a lowercase letter as native HTML elements and elements starting with a capital letter as components defined by you.

This is how `React` distinguishes a built-in elements from user-defined components.


## Expression interpolation

You can embed any JavaScript expression in JSX by wrapping it in curly braces:

```JSX
const sizes = ['small', 'medium', 'large', 'huge'];
const langs = ['Hello', 'Hola'];

<Welcome size={ sizes[3] }>
  { langs[0] }, you!
</Welcome>
```
