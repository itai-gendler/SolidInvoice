---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor opens registration without an invitation
  kind: actor
  actor: visitor
  entities:
  - {entity: invitation, effect: reads, facts: []}
  contexts:
    web: {place: 'web::sign-in::registration'}
- text: Registration is not allowed on this install
  kind: condition
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::registration'}
---

# Refuse registration while it is not allowed

## Trigger

Someone tries to register on an install that does not allow it.

## Outcome

No account is created.
