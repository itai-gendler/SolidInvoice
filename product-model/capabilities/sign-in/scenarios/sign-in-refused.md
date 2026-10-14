---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor enters an email and password that do not match an account
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
- text: The Product refuses and stays on the sign-in page
  kind: condition
  actor: visitor
  entities:
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
---

# Refuse wrong credentials

## Trigger

The credentials are wrong.

## Outcome

Nobody is signed in.
