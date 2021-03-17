---
title: "Quickstart"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "prologue"
weight: 020
toc: true
---

Staq comes in two parts, a client side and a server side library. This
guide will show you how to create a basic SaaS app from scratch using
Staq for both sides. It will take five or ten minutes.

Note: If you don’t have a Stripe account or don’t want to enable
payments, you can skip the payments configuration in `index.js` and the
entire Server section.

## Client

1. First let’s create a React project with `create-react-app`.

   ```sh
   create-react-app staq-quickstart && cd staq-quickstart
   ```


2. Then let’s install dependencies. We need the Staq.js client side
   library, Firebase, and React Router.

   ```sh
   yarn add @staqjs/client firebase react-router-dom
   ```

3. To install Staq into our app, we need to add some code to two
   files. The first is `index.js`, where we configure the library and wrap
   our app in a Staq function call. This is what the updated `index.js`
   should look like.

   ```jsx
   // src/index.js

   import React from 'react';
   import ReactDOM from 'react-dom';
   import './index.css';
   import App from './App';
   import * as serviceWorker from './serviceWorker';
   import { initStaq, withStaq } from '@staqjs/client'
   
   // Pass in configuration options
   initStaq({
     SiteTitle: 'Storyblanks',
     Template: {
       Name: 'One',
       Config: {
         Navbar: {
           MenuLinks: [
             { to: '/pricing', text: 'Pricing' },
             { to: '/signin', text: 'Login' },
           ],
           GetStartedLink: '/signup',
         },
         Hero: {
           PrimaryText: 'SaaS apps are great!',
           SecondaryText: 'You should totally subscribe',
           PrimaryLink: { text: 'Get Started', to: '/signup' },
         },
       },
     },
     FirebaseConfig: {
       // your Firebase config object
     },
   })
   
   ReactDOM.render(
     // Wrap the application with a Staq.js context
     withStaq(
       <React.StrictMode>
         <App />
       </React.StrictMode>
     ),
     document.getElementById('root')
   );
   
   // If you want your app to work offline and load faster, you can change
   // unregister() to register() below. Note this comes with some pitfalls.
   // Learn more about service workers: https://bit.ly/CRA-PWA
   serviceWorker.unregister();
   ```


   The other file we need to update is `App.js`. This is where we use
   Staq to render basic routes like landing page, sign in page, sign
   out page, etc.

   Remove the markup in that file, and replace it with a Router and a
   Staq component. Here’s what the updated file should look like.

   ```jsx
   // src/App.js

   import React from 'react';
   import logo from './logo.svg';
   import './App.css';
   import { Router } from 'react-router-dom'
   import { StaqRoutes } from '@staqjs/client'
      
   function App() {
     return (
       <Router>
         <StaqRoutes />
       </Router>
     );
   }
      
   export default App;
   ```

4. That’s it! On the client side anyway. Start up your app with `yarn
   start` and check out the pages at `/`, `/signup`, and `/signin`.


## Server

1. If you don’t have the Firebase CLI yet, follow [this guide](https://firebase.google.com/docs/cli) to install it.

2. Initialize Firebase in the `staq-quickstart` project.

   ```sh
   firebase init
   ```

3. Install the Staq server side library.

   ```sh
   yarn add @staqjs/server
   ```

4. Add Staq server code to `functions/index.js` to support everything
   needed for subscription payments with Stripe. Replace what’s in the
   file with the following.

   ```js
   const { initStaq, createStripeCustomerPortalSession, stripeCustomer } = require('@staqjs/server')

   initStaq({
     gcpProjectNumber:   // your Google Cloud project number
     stripeTrialPriceId: // the ID of the default Stripe Price users will be subscribed to
     useTrial: false,    // whether or not user should be started on a trial
   })
   
   exports.stripeCustomer = stripeCustomer
   exports.createStripeCustomerPortalSession = createStripeCustomerPortalSession
   ```

5. Deploy your Firebase functions.

   ```sh
   firebase deploy --only functions
   ```
