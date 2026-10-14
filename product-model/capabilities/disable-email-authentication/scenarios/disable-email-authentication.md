---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Disable under Email Authentication
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Email authentication]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
- text: The Product turns email authentication off, clearing the backup codes when no other method remains
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Email authentication, Backup codes]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
---

# Disable email authentication

## Trigger

The User no longer wants emailed codes.

## Outcome

Sign-in no longer asks for an emailed code.
