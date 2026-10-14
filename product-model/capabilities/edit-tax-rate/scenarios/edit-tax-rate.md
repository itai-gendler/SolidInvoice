---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the name, rate, type, category or compounding and saves
  kind: actor
  actor: user
  entities:
  - {entity: tax-rate, effect: reads, facts: [Name, Rate]}
  contexts:
    web: {place: 'web::company-workspace::tax-rate-form'}
- text: The Product saves the tax rate
  kind: product
  actor: user
  entities:
  - {entity: tax-rate, effect: changes, facts: [Name, Rate, Type, Category, Compound]}
  contexts:
    web: {place: 'web::company-workspace::tax-rate-form'}
---

# Edit a tax rate

## Trigger

A tax rate changes, for example a new VAT percentage.

## Outcome

Line taxes chosen from now on use the new values; issued invoices and quotes keep the values they were issued with.
