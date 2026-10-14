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
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The User sets the invoice date and due terms and enters line items with their taxes, a discount, withholding and adjustments, terms and notes
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The User chooses Publish
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product creates the invoice and issues it as Pending without emailing it
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Pending, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
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

# Create and publish an invoice

## Trigger

The invoice is ready but the User will deliver it another way.

## Outcome

The invoice is Pending and payment is expected; nothing has been emailed.
