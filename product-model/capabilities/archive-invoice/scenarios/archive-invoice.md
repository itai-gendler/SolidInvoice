---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Archive on a paid invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product archives the invoice and lists it under Archived
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Paid, to: Archived, facts: [Listed in Archived]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product returns to the invoice list
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
---

# Archive a paid invoice from its page

## Trigger

A paid invoice is finished with.

## Outcome

The invoice is Archived and listed under the Archived tab; no further changes are offered on it.

## Edge cases

- Draft and cancelled invoices can be archived from their page too; pending and overdue ones cannot.
