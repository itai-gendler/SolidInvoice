---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor enters their email and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
- text: The account uses email authentication or an authenticator app, and this device is not trusted
  kind: condition
  actor: visitor
  entities:
  - {entity: user, effect: reads, facts: [Email authentication, Authenticator app, Trusted device]}
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
- text: The Visitor enters the code from their email or app, or a backup code, and may trust the device for 30 days
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
- text: The Product signs the person in
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: changes, facts: [Backup codes, Trusted device]}
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
references:
- kind: doc
  role: intent
  target: docs/docs/using-solidinvoice/two-factor-authentication.md
---

# Sign in with a second factor

## Trigger

An account protected by two-factor authentication signs in.

## Outcome

The person is signed in; a used backup code no longer works.
