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
    web: {place: 'web::company-workspace::quote-editor'}
- text: The User enters line items with their taxes, a discount, withholding and adjustments, terms and notes
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The User chooses Save as Draft
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product creates the quote as a Draft with the next quote number
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: creates, to: Draft, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  contexts:
    web: {place: 'web::company-workspace::quote-editor'}
- text: The Product shows the new quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Save a new quote as a draft

## Trigger

The User starts a quote they are not ready to issue.

## Outcome

A Draft quote exists for the client and can still be changed freely.
