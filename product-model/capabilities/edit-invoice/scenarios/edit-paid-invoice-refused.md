---
kind: validation
routes:
  web: Web
steps:
- text: The User opens the editor of a paid invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
- text: The Product refuses because the invoice is paid and returns to the invoice list with a warning
  kind: condition
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-list'}
---

# Refuse to edit a paid invoice

## Trigger

The User tries to change a paid invoice.

## Outcome

The paid invoice is unchanged.
