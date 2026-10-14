---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Enable under Email Authentication
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Email authentication]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
- text: The Product turns email authentication on and creates backup codes when there are none
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Email authentication, Backup codes]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
---

# Enable email authentication

## Trigger

The User wants a second factor.

## Outcome

Sign-in asks for an emailed code.
