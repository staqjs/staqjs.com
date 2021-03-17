---
title: "withFirebase"
description: ""
lead: ""
date: 2020-10-06T08:49:31+00:00
lastmod: 2020-10-06T08:49:31+00:00
draft: false
images: []
menu:
  docs:
    parent: "api-reference"
weight: 240
toc: true
---

The `withFirebase` function is a higher-order component that injects a
`firebase` prop into the component given to it as an argument. The
`firebase` prop provides access to methods for interacting with
various Firebase services like Firestore and Authentication.

## Import

```jsx
import { withFirebase } from '@staqjs/client'
```

## API

The `firebase` prop supplied by `withFirebase` supports the following
properties.

#### doCreateUserWithEmailAndPassword

**type:** function

**signature:** `(email: string, password: string) => Promise<object>`

This function takes an email and password and uses the Firebase
[Password-Based
Accounts](https://firebase.google.com/docs/auth/web/password-auth) API
to create a new user. It returns a Promise which contains the new user
if successful, and an error if unsuccessful.


#### doSignInWithEmailAndPassword

**type:** function

**signature:** `(email: string, password: string) => Promise<UserCredential>`

This function takes an email and password and uses the Firebase
[Password-Based
Accounts](https://firebase.google.com/docs/auth/web/password-auth) API
to authenticate the user with the given email and password. The method
returns a Promise which, if the authentication is successful, contains
a
[UserCredential](https://firebase.google.com/docs/reference/js/firebase.auth#usercredential),
and if not successful, and an error if the login was not successful.


#### doSignOut

**type:** function

**signature:** `() => Promise<void>`

This function signs the user out.


#### doPasswordReset

**type:** function

**signature:** `(email: string) => Promise<void>`

This function sends a password reset email to the given email address
by calling the
[sendPasswordResetEmail](https://firebase.google.com/docs/reference/js/firebase.auth.Auth#sendpasswordresetemail)
method of Firebase Auth.


#### doPasswordUpdate

**type:** function

**signature:** `(newPassword: string) => Promise<void>`

This function updates the user's password by calling the
[updatePassword](https://firebase.google.com/docs/reference/js/firebase.User#updatepassword)
method of the currently signed in user.


#### doSendEmailVerification

**type:** function

**signature:** `(newPassword: string) => Promise<void>`

This function sends a verification email to the currently signed in
user. The [BaseUrl](/api/init-staq#baseurl) Staq.js configuration
parameter is used for the callback link.


#### onAuthUserListener

**type:** function

**signature:** `(next: function, fallback: function) => Promise<void>`

This function sets up a listener for changes in the authentication
state of the current user. When a sign in is successful, the listener
will call `next` and pass in the `currentUser` object.

When the current user is signed out, this function will call
`fallback` with no arguments.


#### user

**type:** function

**signature:** `(uid: string) => DocumentReference`

Returns a
[DocumentReference](https://firebase.google.com/docs/reference/js/firebase.firestore.DocumentReference)
to the document at path `uid` in the `users` collection.


#### users

**type:** function

**signature:** `() => CollectionReference`

Returns a
[CollectionReference](https://firebase.google.com/docs/reference/js/firebase.firestore.CollectionReference)
to the `users` collection.


#### collection

**type:** function

**signature:** `(collectionName: string) => CollectionReference`

Returns a
[CollectionReference](https://firebase.google.com/docs/reference/js/firebase.firestore.CollectionReference)
to the collection named by `collectionName`.


#### collectionForUser

**type:** function

**signature:** `(collectionName: string, uid: string) => Query<T>`

Returns a
[Query](https://firebase.google.com/docs/reference/js/firebase.firestore.Query)
that resolves to documents in the collection given by `collectionName`
that have a `uid` property equal to the given `uid`.


#### document

**type:** function

**signature:** `(collectionName: string, documentId: string) => DocumentReference`

Returns a
[DocumentReference](https://firebase.google.com/docs/reference/js/firebase.firestore.DocumentReference)
for the document in `collectionName` having `documentId`.


#### addDocumentForUser

**type:** function

**signature:** `(uid: string, collectionName: string, document: object) => Promise<DocumentReference>`

Adds the given document to the collection given by `collectionName`,
and injects a "uid" property and sets the value to `uid`.


#### updateDocument

**type:** function

**signature:** `(collectionName: string, documentId: string, updateFields: object) => Promise<DocumentReference>`

Sets the fields given by `updateFields` in the document having ID
equal to `documentId`, in the collection given by `collectionName`.
