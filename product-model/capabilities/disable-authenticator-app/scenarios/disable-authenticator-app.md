---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Disable under Authenticator App
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Authenticator app]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
- text: The Product turns the authenticator app off, clearing the backup codes when no other method remains
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Authenticator app, Backup codes]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
---

# Disable the authenticator app

## Trigger

The User stops using the app.

## Outcome

Sign-in no longer asks for an app code.
