---
title: "One"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "templates"
weight: 310
toc: true
---


![one-scrot](/one-scrot.png)


## Template Overview

The **One** template ships with five pages:

- Landing
- Pricing
- Signup
- Signin
- Reset Password

Each page listed above includes a navbar and a footer. The primary
background color is configurable across all pages, the navbar, and the
footer.

The landing page ships with four sub-components, organized from top to
bottom:

- Hero
- Benefits
- Pricing
- Call to Action

## Template Configuration

### Background Color

To set the primary background color, define a CSS class named
`bg-primary` with a `background-color` rule.

Ex.

```css
.bg-primary {
  background-color: #EF4444;
}
```


### Hero

The Hero component sits at the top of the landing page and is the
first thing that comes to attention when the site is loaded. It
supports two text slots, two buttons that can be customized to lead to
different URLs, and an image that will occupy the right hand side of
the hero.

```js
Hero: {
  PrimaryText: string,
  SecondaryText: string,
  PrimaryLink: { text: string, to: string },
  SecondaryLink: { text: string, to: string },
  Image: string
}
```

#### API

##### PrimaryText

type: string

This text shows up large and bolded in the top left of the component.

##### SecondaryText

type: string

This text shows up slightly smaller and less prominent underneath the
PrimaryText.

##### PrimaryLink

type: object

This property controls the text and URL behavior of the left hand side
link that shows up underneath the hero text. The `text` property
determines what is displayed inside the link button, and the `to`
property determines where the link leads when clicked.

The `to` property can be a path on the current site, like `'/about'`, or
it can be an absolute URL like `'https://indiehackers.com'`.

##### SecondaryLink

type: object

This property works the same way as the PrimaryLink property, but
controls the text and URL behavior of the right hand side button that
shows up underneath the hero text.

##### Image

type: string

This property is a path to the image that should be displayed on the
right hand side of the hero component.

### Benefits

The Benefits components sits directly underneath the Hero component,
and provides a grid of cards where you can describe what your product
has to offer. The grid can have an arbitrary number of cards, and
adjusts the number of columns responsively to fit them comfortably.

```js
Benefits: [
  {
    MiniTitle: string,
    Title: string,
    Message: string,
  },
]
```

#### API

The configuration object for the Benefits component is a list of
Benefit objects. Each Benefit object supports the following
properties.

##### MiniTitle

type: string

The MiniTitle is a subtle, all-caps title that shows up in the
top-left of each benefit card. It is typically one word, and can be
used to quickly get across the theme of the benefit being described in
the card.

##### Title

type: string

The Title of each benefit card is a prominent bold title that explains
the benefit in a single short sentence.

##### Message

type: string

The Message is a slightly longer (1-2 sentence) description that
explains how your product delivers the benefit in question.

### Pricing

The pricing section appears under the Benefits section and lays out
the prices and corresponding feature sets for different plans your
product offers. Or, if it is not a subscription product, the pricing
cards can show separate products along with their prices.

```js
Pricing: {
  Title: string,
  Plans: [
    {
      Title: string,
      Subtitle: string,
      Price: {
      Value: string, 
        Description: string, 
        Subdescription: string
      },
      Features: [
        { Text: string },
      ],
      CtaLink: { 
        To: '/signup', 
        Text: string
      },
    }
  ]
}
```

#### API

##### Title

type: string

This property sets the title text for the Pricing section. It appears
large, centered, and bolded.

##### Plans

type: Array<object>

This property supports an arbitrary number of `Plan` objects which
determine the content for each plan card rendered by the Pricing
component.

Plan object properites follow.

##### Plan.Title

type: string

The plan title appears prominently bolded at the top left of each plan
card.

##### Plan.Subtitle

type: string

The plan subtitle appears in regular text underneath the plan title.

##### Plan.Price

type: object

The Price propery of each plan object determines how the price is
displayed on the plan card.

Plan card price object properties follow.

##### Plan.Price.Value

type: string

The price value property is displayed large and bold in the center of
the plan card. It is typically used to display the currency-denoted
price of the plan or product.

##### Plan.Price.Description

type: string

This is a small text field that appears to the top-right of the plan
value. It can be used to show that the price is a subscription that
occurs per unit time, as in `/mo`. Or, it could be used to display the
sub-dollar value of the price, as in `99`.

##### Plan.Price.Subdescription

type: string

This field serves the same purpose as the plan description, but shows
up at the bottom right.

##### Plan.Features

type: Array<string>

This property is a list of strings that describe features offered by
the plan in question. The features show up in a column underneath the
plan price.

##### Plan.CtaLink

type: object

The plan call-to-action link appears as a button at the bottom of the
plan card. It can be use to redirect to a sign-up or a checkout page.

The CTA link properties follow.

##### Plan.CtaLink.Text

type: string

This is button's text content.

##### Plan.CtaLink.To

type: string

This property defines the URL behavior of the link. It can be a
relative path on the current site, like `/signup`, or an absolute URL,
like `https://indiehackers.com`.

### Call To Action

The CallToAction component appears below the Pricing section, and
displays a call-to-action message along with a button that should
redirect the user to a page where they can take a meaningul action,
like signing up or making a purchase.

```js
CallToAction: {
  Title: string,
  Link: {
    Text: string,
    To: string
  }
}
```

#### API

##### Title

type: string

This property determines the title text which shows up bold and
centered at the top of the component.

##### Link

type: object

The CallToAction Link property determines the text content and URL
behavior of the link, which shows up centered underneath the title.

Link properties follow.

##### Link.Text

type: string

This property determines the text in the link button.

##### Link.To

type: string

This property determines where the link leads when clicked. The value
can be either a relative path on the current site, like `/signup`, or
an absolute URL, like `https://indiehackers.com`.

### Footer

The Footer component can contain links to useful pages like Terms of
Service, Contact, Privacy Policy, etc., as well as a copyright
message and an optional plug for the Staq.js project.

```js
Footer: {
  Columns: [
    {
      Title: string,
      Links: [
        Text: string,
        To: string
      ],
    }
  ],
  Copyright: string,
  PoweredByStaq: boolean
}
```

#### API

##### Columns

type: Array<object>

The Footer supports an arbitrary number of columns that group links by
category. For example, you might have a "Company" column with links to
'About', 'Jobs', and 'Blog'.

Column object properties follow.

##### Column.Title

type: string

The column title will show up bolded above the vertical list of column
links.

##### Column.Links

type: Array<object>

This property is a list of links to show in the column.

Column Link object properties follow.

##### Column.Link.Text

type: string

This property determines the text in the link button.

##### Column.Link.To

type: string

This property determines where the link leads when clicked. The value
can be either a relative path on the current site, like `/signup`, or
an absolute URL, like `https://indiehackers.com`.

##### Copyright

type: string

This property determines what message to display in the bottom left of
the footer next to the copyright symbol. It is typically the name of
the company and the current year. For example, `'2021 Staq.js'`, if
Staq.js were a company :)

##### PoweredByStaq

type: boolean

If true, a subtle `Powered by staqjs` message is displayed in the bottom
right of the footer.

## Example Usage

```js
initStaq({
  Template: {
    Name: 'One',
    Config: {
      Navbar: {
        MenuLinks: [
          { To: '/pricing', Text: 'Pricing' },
          { To: '/signin', Text: 'Login' },
        ],
        GetStartedLink: '/signup',
      },

      Hero: {
        PrimaryText: 'SaaS apps are great!',
        SecondaryText: 'You should totally subscribe',
        PrimaryLink: { Text: 'Get Started', To: '/signup' },
        PrimaryLink: { Text: 'Learn More', To: '/about' },
        Image: '/images/hero.png'
      },

      Benefits: [
        {
          MiniTitle: 'ANALYTICS',
          Title: 'Improve business insight',
          Message: 'See your data in a whole new way'
        },
        {
          MiniTitle: 'PARTIES',
          Title: 'Bring together friends and family',
          Message: 'Nothing has ever been more fun!'
        },
        {
          MiniTitle: 'FINANCIALS',
          Title: 'Manage money better',
          Message: 'Get granular controls over all your payment flow'
        },
      ],

      Pricing: {
        Title: 'Pricing',
        Plans: [
          {
            Title: 'Free Trial',
            Subtitle: 'Try risk free today!',
            Price: { 
              Value: '$0', 
              Description: '', 
              Subdescription: '' 
            },
            Features: [
              { Text: '5 completely custom items' },
              { Text: 'Export to PDF' },
            ],
            CtaLink: { 
              To: '/signup', 
              Text: "Sign Up, It's Free" 
            },
          },
          {
            Title: 'Standard Package',
            Subtitle: '',
            Price: {
              Value: '$5',
              Description: 'One time purchase',
              Subdescription: '',
            },
            Features: [
              { Text: '25 completely custom items' },
              { Text: 'Export to PDF' },
            ],
            CtaLink: { 
              To: '/signup', 
              Text: 'Checkout Now' 
            },
          },
        ],
      },

      CallToAction: {
        Title: 'Get started for free',
        ActionText: 'Get Started',
        ActionLink: '/signup',
      },

      Footer: {
        Columns: [
          {
            Title: 'Company',
            Links: [
              { 
                Text: 'Terms and Conditions', 
                To: '/terms' 
              },
              { 
                Text: 'Privacy Policy', 
                Link: '/privacy' 
              },
            ],
          },
          {
            Title: 'Contact',
            Links: [{ 
              Text: 'support@company.com', 
              To: 'mailto:support@company.com' 
            }],
          },
        ],
        Copyright: '2021 Staq.js',
        PoweredByStaq: true,
      },
    }
  }
})
```
