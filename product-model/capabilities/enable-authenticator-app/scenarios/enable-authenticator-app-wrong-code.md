---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a code that does not match
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Authenticator app]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
- text: The Product refuses and keeps the app off
  kind: condition
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Authenticator app]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
---

# Refuse a wrong app code

## Trigger

The app was set up wrongly.

## Outcome

The authenticator app stays off.
