---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Revoke Trust
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Trusted device]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
- text: The Product forgets the trusted device
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Trusted device]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
---

# Revoke trust in a device

## Trigger

A device should no longer skip the second factor.

## Outcome

The next sign-in on it asks for a code.
