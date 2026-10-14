---
kind: primary
routes:
  web: Web
steps:
- text: The User selects one or more tax rates, chooses Delete and confirms
  kind: actor
  actor: user
  entities:
  - {entity: tax-rate, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::tax-rates'}
- text: The Product deletes the tax rates
  kind: product
  actor: user
  entities:
  - {entity: tax-rate, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::tax-rates'}
---

# Delete tax rates

## Trigger

A tax no longer applies.

## Outcome

The rates are no longer offered for new line items.
