---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Resume on a paused recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Recurring type]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
- text: The Product makes the recurring invoice active again
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Paused, to: Active, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Resume a paused recurring invoice

## Trigger

Billing should continue.

## Outcome

The recurring invoice is Active; generation continues from the next matching date, with no catch-up for dates missed while paused.
