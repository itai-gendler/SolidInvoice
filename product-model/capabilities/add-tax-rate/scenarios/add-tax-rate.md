---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the name, rate, type and category and whether it compounds, and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::tax-rate-form'}
- text: The Product creates the tax rate
  kind: product
  actor: user
  entities:
  - {entity: tax-rate, effect: creates, facts: [Name, Rate, Type, Category, Compound]}
  contexts:
    web: {place: 'web::company-workspace::tax-rate-form'}
- text: The Product returns to the tax rates
  kind: product
  actor: user
  entities:
  - {entity: tax-rate, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::tax-rates'}
---

# Add a tax rate

## Trigger

The company charges a tax it has not set up yet.

## Outcome

The rate is offered on line items and as withholding or adjustment on invoices, quotes and recurring invoices.
