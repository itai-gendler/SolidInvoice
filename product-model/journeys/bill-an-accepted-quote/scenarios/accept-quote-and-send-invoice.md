---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User chooses Accept on a pending quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number, Total]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
  capability: accept-quote
- text: The Product marks the quote accepted and creates a draft invoice from it
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Accepted, facts: []}
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
  capability: accept-quote
- text: The Product takes the User to the new invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: accept-quote
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

# Accept a quote, then send its invoice

## Trigger

The client agrees to a quote.

## Outcome

The client's contacts have the invoice for the accepted quote.
