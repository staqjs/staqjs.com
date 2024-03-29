---
title: "initStaq"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "api-reference"
weight: 210
toc: true
---

`initStaq` is the function that initializes the Staq.js client
library. It takes a configuration object which is used to set values
for things like

- the current template
- payments
- Firebase

It should be called before `ReactDOM.render`.

## Import

```jsx
import { initStaq } from '@staqjs/client'
```

## API

The configuration object passed to `initStaq` supports the following
properties:

#### SiteTitle

**type:** string

Used as the value in the `<title>` tag of the site


#### BaseUrl

**type:** string

The domain where the app is hosted. This value is used in various
places, for example as the callback URL for email verification links.


#### UserHome

**type:** string

Should be the URL path for the page users are directed to on login.


#### Template

**type:** object

An object used to configure options for the template.


#### Payments

**type:** object

An object used to configure options for payments.


#### FirebaseConfig

**type:** object

The object used to configure the Firebase SDK.


#### UserDefaults

**type:** object

An object with default properties to set for new users.


## Example Usage

```jsx
import { initStaq, withStaq } from '@staqjs/client'

initStaq({
  SiteTitle: 'My Site',
  UserHome: '/dashboard',
  Template: {
    // ...
  },
  Payments: {
    // ...
  },
  FirebaseConfig: {
    // ...
  },
  UserDefaults: {
    // ...
  }
})
```
