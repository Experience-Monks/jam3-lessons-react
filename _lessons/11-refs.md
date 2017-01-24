---
layout: lesson
title: Refs
slug: refs
references:
  - title: 'Refs and the DOM'
    url: 'https://facebook.github.io/react/docs/refs-and-the-dom.html'
---

So far, the only way that parent components can trigger changes within their child components is to pass new props. Another way to communicate with child components is through _refs_.

Through the ref attribute, the parent component can gain access to the child component or element.

Here the property `this.textInput` holds the input element.

``` jsx
<input type="text" ref={(input) => { this.textInput = input; }} />
```

When passed as a _prop_ to a custom component its callback argument would be the mounted instance of the component.

```jsx
<CustomInput ref={(input) => { this.textInput = input; }} />
```

As a rule of thumb, try to use _props_ before trying to use _refs_, so as to make it clear where the state of a component is owned.
