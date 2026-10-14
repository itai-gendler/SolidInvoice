---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to link Google and approves at Google
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Google account]}
  contexts:
    web: {place: 'web::company-workspace::profile'}
- text: The Product links the Google identity to the account
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Google account]}
  contexts:
    web: {place: 'web::company-workspace::profile'}
---

# Link a Google account

## Trigger

The User wants to sign in with Google too.

## Outcome

The profile shows Google as linked; either way of signing in works.
