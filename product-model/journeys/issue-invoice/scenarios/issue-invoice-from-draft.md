---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User picks a client and contacts and enters the invoice
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  - {entity: contact, effect: reads, facts: [First name, Last name, Email]}
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
  capability: create-invoice
- text: The Product creates the invoice as a Draft
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
  capability: create-invoice
- text: The Product takes the User to the new invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: create-invoice
- text: The User chooses Publish and Send
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: send-invoice
- text: The Product issues the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Draft, to: Pending, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: send-invoice
- text: The Product emails the invoice, with its PDF and a link to view and pay it, to the contacts chosen on the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Total, Due date]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Invoice email subject, Invoice BCC address]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: send-invoice
---

# Draft an invoice, then send it

## Trigger

The User bills a client.

## Outcome

The client's contacts have the Pending invoice.
