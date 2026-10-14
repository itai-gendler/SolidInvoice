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
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The User sets the invoice date and due terms and enters line items with their taxes, a discount, withholding and adjustments, terms and notes
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The User chooses Save as Draft
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product creates the invoice as a Draft with the next invoice number and the due date its terms give
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product shows the new invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Save a new invoice as a draft

## Trigger

The User starts an invoice they are not ready to issue.

## Outcome

A Draft invoice exists for the client and can still be changed freely.

## Edge cases

- The form starts with the client's payment terms, or the company default, and the due date they give.
- With exactly one client, that client is picked already.
