---
kind: primary
routes:
  web: Web
steps:
- text: The User selects one or more completed recurring invoices and chooses Reactivate
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Recurring type, End date]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-list'}
- text: The Product makes the selected recurring invoices active again
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Complete, to: Active, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-list'}
---

# Reactivate completed recurring invoices

## Trigger

A finished schedule should run again.

## Outcome

The recurring invoices are Active again.
