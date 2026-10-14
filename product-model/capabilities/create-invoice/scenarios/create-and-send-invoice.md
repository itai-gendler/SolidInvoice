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
- text: The User chooses Save and Send
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product creates the invoice and issues it as Pending
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Pending, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product emails the invoice, with its PDF and a link to view and pay it, to the contacts chosen on the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Total, Due date]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Invoice email subject, Invoice BCC address]}
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

# Create and send an invoice

## Trigger

The invoice is ready to go to the client now.

## Outcome

The invoice is Pending and the chosen contacts have it by email.
