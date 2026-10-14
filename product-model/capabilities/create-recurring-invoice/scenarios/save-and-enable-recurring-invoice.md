---
kind: alternative
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
- text: The User chooses Save and Enable
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The Product creates the recurring invoice as Active
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: creates, to: Active, facts: [Start date, Recurring type, Repeat days, End recurrence, End date, End after occurrences, Payment terms, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-editor'}
- text: The Product shows the new recurring invoice with its upcoming dates
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: [Start date, Recurring type, Repeat days]}
  contexts:
    web: {place: 'web::company-workspace::recurring-invoice-detail'}
---

# Create and enable a recurring invoice

## Trigger

The schedule is ready to run.

## Outcome

The recurring invoice is Active and generates its first invoice on the first matching date from the start date.
