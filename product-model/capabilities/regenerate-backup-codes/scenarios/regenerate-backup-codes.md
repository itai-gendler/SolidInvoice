---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Regenerate Codes
  kind: actor
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Backup codes]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
- text: The Product replaces every backup code with a new set
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Backup codes]}
  contexts:
    web: {place: 'web::company-workspace::two-factor-authentication'}
---

# Regenerate backup codes

## Trigger

The User used or lost codes.

## Outcome

Only the new codes work.

## Edge cases

- The codes can be viewed and downloaded as a text file.
