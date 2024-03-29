---
title: "withAuth"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "api-reference"
weight: 220
toc: true
---

The `withAuth` function is a higher-order component that injects an
`auth` prop into the component given to it as an argument. The `auth`
prop has a reference to the logged in user, so this function is useful
for wrapping components that use or display info based on the current
user.

## Import

```jsx
import { withAuth } from '@staqjs/client'
```

## API

The `auth` prop supplied by `withAuth` supports the following properties.

#### currentUser

**type:** object

An object representing the logged in user, or `undefined` if
no one is logged in.


#### onLogout

**type:** function

**signature:** `(() => void) => void`

This method takes a function to call after logout has been
performed. This is useful for redirecting to home or a signin page
after clicking logout.

Example:

```jsx
const onClickSignOut = () => {
  auth.onLogout(() => {
      history.push('/')
  })
  firebase.doSignOut()
}
```

## Example Usage

```jsx
import { withAuth } from '@staqjs/client'

function Dashboard(props) {
  const { auth } = props

  // ... code ...
}

export default withAuth(Dashboard)
```
