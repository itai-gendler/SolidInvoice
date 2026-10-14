---
kind: primary
routes:
  web: Web
steps:
- text: The User selects a draft recurring invoice and chooses Delete
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Recurring type]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-list'}
- text: The Product deletes the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: removes, from: Draft}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-list'}
---

# Delete recurring invoices from the list

## Trigger

A recurring invoice was created by mistake.

## Outcome

The recurring invoice is gone.

## Edge cases

- Recurring invoices in any status can be deleted from the list.
