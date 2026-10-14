---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses to add a new client and enters its name and a contact's first name, last name and email
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  - {entity: contact, effect: reads, facts: []}
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
- text: The Product creates the client with that contact
  kind: product
  actor: user
  entities:
  - {entity: client, effect: creates, to: Active, facts: [Name, Credit balance]}
  - {entity: contact, effect: creates, facts: [First name, Last name, Email], with: client}
  contexts:
    web: {place: 'web::company-workspace::invoice-editor'}
- text: The Product creates the invoice for the new client as a Draft
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  - {entity: client, effect: reads, facts: []}
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

# Create an invoice for a new client

## Trigger

The invoice is for someone who is not a client yet.

## Outcome

The new client and its contact exist, and the Draft invoice is addressed to that contact.
