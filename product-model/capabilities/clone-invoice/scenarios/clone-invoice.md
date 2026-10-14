---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Clone on an invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, as: original, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product creates a draft invoice with the same client, recipients, line items, discount, taxes, terms, notes, due terms and due date and a new invoice number
  kind: product
  actor: user
  entities:
  - {entity: invoice, as: copy, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  - {entity: invoice, as: original, effect: reads, facts: [Line items, Discount, Withholding and adjustments, Terms, Notes, Payment terms, Due date]}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product shows the new invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, as: copy, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Clone an invoice

## Trigger

The User bills the same things again.

## Outcome

A new Draft invoice dated today exists alongside the original, which is unchanged.
