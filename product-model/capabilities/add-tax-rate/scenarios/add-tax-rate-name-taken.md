---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a name that is already in use and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::tax-rate-form'}
- text: The Product refuses the save and asks for a different name
  kind: condition
  actor: user
  entities:
  - {entity: tax-rate, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::tax-rate-form'}
---

# Refuse a tax rate name already used

## Trigger

The User repeats a tax rate name.

## Outcome

No tax rate is created.
