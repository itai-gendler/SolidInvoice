---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Cancel on an active recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Recurring type]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
- text: The Product cancels the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Active, to: Cancelled, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Cancel an active recurring invoice

## Trigger

The client ended the subscription.

## Outcome

The recurring invoice is Cancelled and generates no more invoices; invoices already generated are unaffected.

## Edge cases

- A draft recurring invoice can be cancelled the same way.
