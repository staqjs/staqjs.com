---
title: "Introduction"
description: ""
lead: ""
date: 2020-10-06T08:48:57+00:00
lastmod: 2020-10-06T08:48:57+00:00
draft: false
images: []
menu:
  docs:
    parent: "prologue"
weight: 010
toc: true
---

## Overview

Staq.js comes as two separate libraries, one for the client and one
for the server. The client-side library, `@staqjs/client`, provides
templates for your marketing website, components for common features
like sign up, sign in and password reset, and helper functions for
interacting with the server and the database.

The server-side library, `@staqjs/server`, provides functions for
interacting with the payments API ([Stripe](https://stripe.com)), which for security reasons
happens on the server.

You can think of Staq.js as a glue framework for three different
technologies:

1. A frontend UI framework ([React](https://reactjs.org))
2. A managed cloud backend ([Firebase](https://firebase.google.com))
3. A payments API ([Stripe](https://stripe.com))

The goal of the project is to minimize the amount of code, time, and
money required to build a web product people pay you for.
