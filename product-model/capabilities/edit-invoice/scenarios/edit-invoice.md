---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the recipients, dates, due terms, line items, discount, withholding and adjustments, terms or notes and saves
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes]}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product saves the invoice and recalculates its totals and balance
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance]}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product shows the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Edit an invoice

## Trigger

An invoice needs correcting.

## Outcome

The invoice carries the new content; its status is unchanged and nothing is emailed.

## Edge cases

- A pending or overdue invoice is not emailed again by saving; Send does that.
