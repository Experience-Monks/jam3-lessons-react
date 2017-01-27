---
layout: lesson
title: Routing
slug: routing
references:
  - title: 'History API on MDN'
    url: 'https://developer.mozilla.org/en-US/docs/Web/API/History'
  - title: 'React Router'
    url: 'https://github.com/ReactTraining/react-router'
---

## General Concepts and Introduction

'react-router' is an npm module. It keeps the UI in sync with the URL. In the below example, going to '/' will load App. Going to '/home' will load App and Home.

React Router module is the most popular implementation to create Single Page Apps with React.

To configure the routes of your app, `JSX` notation can be used among with `Router` and `Route` components provided by React Router.

```jsx
import { Router, Route } from 'react-router';

<Router>
  <Route path="/" component={App}>
    <Route path="home" component={Home} />
    <Route path="about" component={About} />
  </Route>
</Router>
```

Each route receives a component to display and a corresponding path that will trigger the view rendering.


## Creating and displaying views

Each of the views, in this case **Home** and **About**, and what will wrap them, **App** are components we pass through _props_ to our routes.

```jsx
import React from 'react';
import { render } from 'react-dom';
import { Router, Route } from 'react-router';

function App() {
  return (
    <div className="app">
      { this.props.children }
    </div>
  );
}

function Home() {
  return <h1>Home</h1>;
}

function About() {
  return <h1>About</h1>;
}

render(
  document.getElementById('app'),
  <Router>
    <Route path="/" component={App}>
      <Route path="home" component={Home} />
      <Route path="about" component={About} />
    </Route>
  </Router>
);
```

Inside the **App** component, the `children` _prop_ acts as a placeholder for the views that are going to be rendered.


## The Link element

```jsx
import { Link } from 'react-router';


<Link to="/home">Home</Link>
```

The `Link` component is used to navigate through the application. A `Link` is considered active when its content in `to` matches one of the previously defined routes or any of its children routes.

For example, you can use `activeClassName` to put a class on a Link that is being visited

```jsx
import React from 'react';
import { render } from 'react-dom';
import { Link, Router, Route } from 'react-router';

function App() {
  return (
    <div className="app">
      <nav>
        <Link to="home" activeClassName="active">Home</Link>
        <Link to="about" activeClassName="active">About</Link>
      </nav>
      { this.props.children }
    </div>
  );
}

function Home() {
  return <h1>Home</h1>;
}

function About() {
  return <h1>About</h1>;
}

render(
  document.getElementById('app'),
  <Router>
    <Route path="/" component={App}>
      <Route path="home" component={Home} />
      <Route path="about" component={About} />
    </Route>
  </Router>
);
```


## browserHistory and hashHistory

You can configure how you want the url and history of your app to work.

`browserHistory` uses the native History API to manipulate the URL, though it might require additional server configuration to make it handle URLs such as `/` such as `/home/messages`.

```jsx
import { Router, browserHistory } from 'react-router';

<Router history={ browserHistory }>
  ...
</Router>
```

`hashHistory` uses URL hashes like `example.com/#/some/path` and query keys. It requires no additional server configuration.

```jsx
import { useRouterHistory } from 'react-router'
import { createHashHistory } from 'history'

const appHistory = useRouterHistory(createHashHistory)({ queryKey: false });

<Router history={ appHistory }>
  ...
</Router>
```

Usually `browserHistory` is preferred over `hashHistory`.
