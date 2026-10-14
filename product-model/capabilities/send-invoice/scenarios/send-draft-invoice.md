---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Publish and Send on a draft invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product issues the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Draft, to: Pending, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
- text: The Product emails the invoice, with its PDF and a link to view and pay it, to the contacts chosen on the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Total, Due date]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Invoice email subject, Invoice BCC address]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Send a draft invoice

## Trigger

A draft invoice is ready to go to the client.

## Outcome

The invoice is Pending and the chosen contacts have it by email.
