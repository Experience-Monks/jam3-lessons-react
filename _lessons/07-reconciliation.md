---
layout: lesson
title: Reconciliation
slug: reconciliation
references:
  - title: 'Reconciliation article from React official site'
    url: 'https://facebook.github.io/react/docs/reconciliation.html'
---

React provides an easy way to declare how a component will be structured and it will later take care of updating it when a state or a prop has changed generating a new render tree, comparing it with the previous one and only modifying what's necessary.

This task is called **Reconciliation** and it's hard to accomplish in an efficient way.

Understanding that we need to help React figure out which parts of our components are more likely to change is one of the keys of building a performant React web application.
