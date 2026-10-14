---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor follows the confirmation link from the email
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in'}
- text: The Product marks the email verified and signs the person in
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: changes, facts: [Email verified]}
  contexts:
    web: {place: 'web::sign-in'}
---

# Confirm an email address

## Trigger

A new account confirms its address.

## Outcome

The email is verified.
