---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Cancel on a pending invoice and confirms
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product cancels the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Cancelled, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Cancel a pending invoice

## Trigger

The invoice should not be paid.

## Outcome

The invoice is Cancelled and no reminders are sent for it; it can be reopened.

## Edge cases

- Draft and overdue invoices can be cancelled the same way.
