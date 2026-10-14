---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects one or more invoices and chooses Archive
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product lists the selected invoices under Archived, keeping their status
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, facts: [Listed in Archived]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
---

# Archive invoices from the invoice list

## Trigger

The User tidies the active list.

## Outcome

The invoices are listed under Archived with their status unchanged.
