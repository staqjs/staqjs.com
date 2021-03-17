---
title: "withStripe"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "api-reference"
weight: 250
toc: true
---

The `withStripe` function is a higher-order component that injects a
`stripe` prop into the component given to it as an argument. The `stripe`
prop is an instance of the [Stripe
object](https://stripe.com/docs/js/initializing), and should be used
in components dealing with payment flows.

## Import

```jsx
import { withStripe } from '@staqjs/client'
```


## Example Usage

```jsx
import { withStripe } from '@staqjs/client'

function Dashboard(props) {
  const { stripe } = props

  // ... code ...
}

export default withStripe(Dashboard)
```

Also see [getStripeCheckoutSession](/api/get-stripe-checkout-session)
