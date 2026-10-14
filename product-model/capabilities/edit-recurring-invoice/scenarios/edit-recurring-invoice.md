---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the recipients, line items, discount, taxes, terms, notes, due terms or schedule and saves
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Start date, Recurring type, Repeat days, End recurrence, Line items]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The Product saves the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, facts: [Start date, Recurring type, Repeat days, End recurrence, End date, End after occurrences, Payment terms, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The Product shows the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Edit a recurring invoice

## Trigger

A subscription changes.

## Outcome

Invoices generated from now on use the new template and schedule; invoices already generated are unchanged.

## Edge cases

- Editing is offered on draft, active, paused and cancelled recurring invoices.
