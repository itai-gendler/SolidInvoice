---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Archive on a cancelled recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Recurring type]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
- text: The Product archives the recurring invoice and lists it under Archived
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Cancelled, to: Archived, facts: [Listed in Archived]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Archive a cancelled recurring invoice

## Trigger

A recurring invoice is no longer wanted in view.

## Outcome

The recurring invoice is Archived and listed under the Archived tab; the invoices it generated are unaffected.

## Edge cases

- Draft, active and paused recurring invoices can be archived from their page too.
