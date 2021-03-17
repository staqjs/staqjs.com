---
title: "withStaq"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "api-reference"
weight: 230
toc: true
---

The `withStaq` function takes a rendered component tree and surrounds
it with contexts that provide methods and data used by the Staq.js
library. Specifically, the child component tree supplied as the
argument is wrapped in a
[Provider](https://reactjs.org/docs/context.html#contextprovider) for
Firebase, Stripe, and Auth contexts.

## Import

```jsx
import { withStaq } from '@staqjs/client'
```


## Example Usage

The `withStaq` function should usually be called inside `index.js`,
when the application is mounted on the DOM.

```jsx
ReactDOM.render(
  withStaq(
    <ThemeProvider theme={Theme}>
      <App />
    </ThemeProvider>
  ),
  document.getElementById('root')
)
```
