---
kind: primary
routes:
  web: Web
steps:
- text: The User picks an active client and the contacts to send to
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: contact, effect: reads, facts: [First name, Last name, Email]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The User enters line items with their taxes, a discount, withholding and adjustments, terms, notes and due terms
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The User sets the start date, the recurring type with its days, and how the recurrence ends
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The User chooses Save as Draft
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The Product creates the recurring invoice as a Draft
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: creates, to: Draft, facts: [Start date, Recurring type, Repeat days, End recurrence, End date, End after occurrences, Payment terms, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The Product shows the new recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Save a new recurring invoice as a draft

## Trigger

The User prepares a subscription they want to review before it runs.

## Outcome

A Draft recurring invoice exists; it generates nothing until activated.
