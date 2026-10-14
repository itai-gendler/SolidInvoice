---
kind: primary
routes:
  web: Web
steps:
- text: The User filters the invoice list and chooses Export with a format
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product downloads the listed invoices in that format
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Invoice date, Due date, Total, Balance]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
---

# Export the invoice list

## Trigger

The User needs the data elsewhere.

## Outcome

A file with the listed rows downloads at once.

## Edge cases

- Every list offers the same export: quotes, clients, payments and the others.
