---
kind: primary
routes:
  web: Web
steps:
- text: The User selects a draft invoice and chooses Delete
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product deletes the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: removes, from: Draft}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
---

# Delete invoices from the invoice list

## Trigger

An invoice was created by mistake.

## Outcome

The invoice is gone.

## Edge cases

- Invoices in any status can be deleted from the list; their payments go with them.
