---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters an email and password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::registration'}
- text: The Product creates the account and signs the person in
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: creates, facts: [Email, Password, Email verified]}
  contexts:
    web: {place: 'web::sign-in::registration'}
---

# Register a new account

## Trigger

Someone new wants to use SolidInvoice.

## Outcome

The account exists and the person continues to onboarding.
