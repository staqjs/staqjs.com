---
title: "getStripeCheckoutSession"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "api-reference"
weight: 260
toc: true
---

This function is a helper for creating a [Stripe Checkout
Session](https://stripe.com/docs/api/checkout/sessions). It pings a
corresponding backend function to create a short-term session that can
be used to allow a customer to pay for one-time purchases or
subscriptions through [Stripe
Checkout](https://stripe.com/docs/payments/checkout).

## Import 

```jsx
import { getStripeCheckoutSession } from '@staqjs/client'
```

## API

**type:** function

**signature:** `(uid: string, customerId: string, priceId: string) => Promise<Session>`

This function takes a user ID, a Stripe
[Customer](https://stripe.com/docs/api/customers) ID, and a Stripe
[Price](https://stripe.com/docs/api/prices) ID.

When successful, the function returns a Promise which resolves to the
[Session](https://stripe.com/docs/api/checkout/sessions/object)
object. Use the session object to call
[redirectToCheckout](https://stripe.com/docs/js/checkout/redirect_to_checkout).

When unsuccessful, the Promise resolves to an error.

## Example Usage

```jsx
import { getStripeCheckoutSession, withAuth, withStripe } from '@staqjs/client'

function Dashboard(props) {
  const { auth, stripe } = props
  const [isLoading, setLoading] = useState(false)
  
  const onClickCheckoutBtn = () => {
    setLoading(true)
    getStripeCheckoutSession(
      auth.currentUser.uid,
      auth.currentUser.stripeCustomerId,
      'price_1I2nbcA8NzJgebq9qZajEq0E'
    )
      .then((result) => {
        setLoading(false)
        return stripe.redirectToCheckout({ sessionId: result.data.id })
      })
      .catch((error) => {
        console.error(error)
        // error handling
      })
  }

  // ... code ...
}

export default withAuth(withStripe(Dashboard))
```
