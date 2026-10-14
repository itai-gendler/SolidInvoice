---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User picks a client and contacts and enters the template and schedule
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: contact, effect: reads, facts: [First name, Last name, Email]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
  capability: create-recurring-invoice
- text: The Product creates the recurring invoice as a Draft
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: creates, to: Draft, facts: [Start date, Recurring type, Repeat days, End recurrence, End date, End after occurrences, Payment terms, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
  capability: create-recurring-invoice
- text: The Product takes the User to the new recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
  capability: create-recurring-invoice
- text: The User chooses Activate
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Start date, Recurring type]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
  capability: activate-recurring-invoice
- text: The Product activates the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Draft, to: Active, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
  capability: activate-recurring-invoice
---

# Draft a recurring invoice, then activate it

## Trigger

A client takes out a subscription.

## Outcome

The recurring invoice is Active and will generate invoices on its schedule.
