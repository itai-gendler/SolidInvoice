---
kind: alternative
routes:
  web: Web
steps:
- text: The User opens an invoice from the invoice list
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product shows the invoice with its internal notes and the abilities its status allows
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Line items, Notes, Total, Balance]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# A user opens an invoice

## Trigger

The User checks an invoice.

## Outcome

The User sees the invoice, including the notes the client never sees.
