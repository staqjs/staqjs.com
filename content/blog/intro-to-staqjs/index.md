---
title: "Introducing Staq.js 👋"
date: 2021-03-14T09:19:42+01:00
lastmod: 2020-15-04T09:19:42+01:00
draft: false
weight: 50
images: []
contributors: ["Matt Roll"]
---

In the first half of 2020, I built three web applications. They all
used the same stack: React and Firebase. The combination of these two
tools is the fastest way I know how to build out prototypes for web
app ideas.

But I noticed something frustrating while building these three
projects. I had to write a bunch of the same code for each one. In
fact, I found myself straight up copying files from the first project
to the other two. And the code I was copying was code that has to
exist in one form or another in just about every web application out
there: components and logic for handling users, helper functions for
interacting with the database, backend logic for managing subscription
billing, and standard components like the landing page and footer.

So I decided to create Staq. An open source library I can call into
whenever I need standard SaaS building blocks.

I initially toyed with the idea of charging for Staq as a code
generator. But I discovered I care a lot about the potential this tool
has for unlocking productivity on the web, and I don’t want to limit
the userbase to people who can justify paying to use it.

When I look at my experience building out product ideas, the boring
and time consuming part is the work necessary to hook together these
amazing services like Stripe and Firebase that make it possible to run
a successful business from your couch with almost no startup
capital. I think this type of boring plumbing is a significant barrier
to entry that stops a lot of potentially great and profitable
businesses from getting started. And just like the role Stripe and
Firebase play in payments and hosting, I want there to be a product
that lets you get over that barrier quickly and without upfront
payment. As an open source project that is available as a free npm
package, I think Staq can fill that role.

The project is super early and has a long way to go, but the proof
concept is working. You can follow the Getting Started guide on the
documentation site and have a SaaS app up and running in minutes,
complete with user auth and subscription billing. I’m even using Staq
to power a side project of mine over at [storyblanks.com](https://storyblanks.com).
