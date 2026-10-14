---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Pause on an active recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Recurring type]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
- text: The Product pauses the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Active, to: Paused, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Pause an active recurring invoice

## Trigger

Billing must stop for a while.

## Outcome

The recurring invoice is Paused with its template and schedule kept; nothing is generated while it is paused.
