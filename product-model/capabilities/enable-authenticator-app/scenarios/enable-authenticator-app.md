---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Enable under Authenticator App, scans the code or enters the secret in their app, and enters the code it shows
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Authenticator app]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
- text: The Product turns the authenticator app on and creates backup codes when there are none
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Authenticator app, Backup codes]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
---

# Enable an authenticator app

## Trigger

The User wants app-based codes.

## Outcome

Sign-in asks for a code from the app.
