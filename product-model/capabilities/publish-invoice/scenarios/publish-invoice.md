---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Publish on a draft invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product issues the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Draft, to: Pending, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Publish a draft invoice

## Trigger

A draft invoice is ready.

## Outcome

The invoice is Pending and payment is expected; its tax rates and currency are fixed.
