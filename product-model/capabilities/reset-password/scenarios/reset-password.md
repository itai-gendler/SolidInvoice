---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their email
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::password-reset'}
- text: The Product emails a reset link when the email has an account
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::sign-in::password-reset'}
- text: The Visitor follows the link and chooses a new password
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web: {place: 'web::sign-in::password-reset'}
- text: The Product saves the new password
  kind: product
  actor: visitor
  entities:
  - {entity: user, effect: changes, facts: [Password]}
  contexts:
    web: {place: 'web::sign-in::password-reset'}
---

# Reset a forgotten password

## Trigger

Someone forgot their password.

## Outcome

The account has the new password.
