---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor follows an expired or altered confirmation link
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in'}
- text: The Product refuses and returns to the sign-in page
  kind: condition
  actor: visitor
  entities:
  - {entity: user, effect: reads, facts: [Email verified]}
  contexts:
    web: {place: 'web::sign-in::sign-in-page'}
---

# Refuse an expired or invalid link

## Trigger

The link no longer works.

## Outcome

The email stays unverified.
