---
layout: lesson
title: Pure components
slug: pure-components
references:
  - title: 'React.PureComponent official documentation'
    url: 'https://facebook.github.io/react/docs/react-api.html#react.purecomponent'
  - title: 'Stateless Components'
    url: 'https://medium.com/@joshblack/stateless-components-in-react-0-14-f9798f8b992d#.dkm84h7pq'
---

When you know a component will always render the same result given the same props and state you can extend from `React.PureComponent` instead of `React.Component` which implements `shouldComponentUpdate()` with a shallow compare on them.
