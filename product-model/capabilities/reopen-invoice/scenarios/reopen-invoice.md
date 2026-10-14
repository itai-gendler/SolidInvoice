---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reopen on a cancelled invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product returns the invoice to draft
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Cancelled, to: Draft, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Reopen a cancelled invoice

## Trigger

A cancelled invoice is needed after all.

## Outcome

The invoice is a Draft again and can be changed and issued.
