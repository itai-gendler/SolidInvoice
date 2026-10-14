---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their current password and a new one
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::profile'}
- text: The Product saves the new password
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Password]}
  contexts:
    web: {place: 'web::company-workspace::profile'}
---

# Change one's password

## Trigger

The User wants a new password.

## Outcome

The new password is needed from the next sign-in.
