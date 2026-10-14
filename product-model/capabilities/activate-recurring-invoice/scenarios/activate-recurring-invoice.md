---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Activate on a draft recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Start date, Recurring type]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
- text: The Product activates the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Draft, to: Active, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Activate a draft recurring invoice

## Trigger

A draft subscription is ready to run.

## Outcome

The recurring invoice is Active and the scheduler picks it up on its next run.
