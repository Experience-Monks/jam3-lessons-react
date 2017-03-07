---
layout: lesson
title: React.createElement
slug: react-create-element
references:
  - title: 'React Top Level API'
    url: 'https://facebook.github.io/react/'
  - title: 'Thinking in React'
    url: 'https://facebook.github.io/react/docs/react-api.html#createelement'
  - title: 'JavaScript modules, module loaders and module bundlers'
    url: http://jvandemo.com/a-10-minute-primer-to-javascript-modules-module-formats-module-loaders-and-module-bundlers/
---

Components are composed by _elements_, other components or a combination of both.

Elements we create will be reflected as nodes in our web app and we do it by calling `React.createElement` like this:

```js
import React from 'react';

React.createElement(
  'div',
  { className: 'wrapper' },
  [ React.createElement('p', null, 'Lorem ipsum') ]
);
```

Notice the first argument of this method is the HTML tag name of the element, the second one an object containing attributes and _props_ and the third one a child element or an array of them. The output of the sample code from above should look like this.

```html
<div class="wrapper">
  <p>Lorem Ipsum</p>
</div>
```

Since `class` and `for` are reserved words in JavaScript `className` and `htmlFor` are used respectively to avoid parsing errors.

**Note:** You might have noticed an `import` statement at the beginning of the sample code from above. If you are not familiar with modules and bundlers, you can check out the article in the **References** section here.
