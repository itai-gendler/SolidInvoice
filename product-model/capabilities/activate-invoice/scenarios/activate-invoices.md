---
kind: primary
routes:
  web: Web
steps:
- text: The User selects one or more invoices that were archived from the list and chooses Activate
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product lists the selected invoices among the active invoices again
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, facts: [Listed in Archived]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
---

# Activate archived invoices

## Trigger

An archived invoice is needed again.

## Outcome

The invoices are back in the active list; their status is unchanged.
