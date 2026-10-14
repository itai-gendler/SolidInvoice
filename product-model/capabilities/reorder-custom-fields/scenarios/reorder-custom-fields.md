---
kind: primary
routes:
  web: Web
steps:
- text: The User drags fields into a new order
  kind: actor
  actor: user
  entities:
  - {entity: custom-field, effect: reads, facts: [Label, Position]}
  contexts:
    web: {place: 'web::company-workspace::custom-fields'}
- text: The Product saves the new positions
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: changes, facts: [Position]}
  contexts:
    web: {place: 'web::company-workspace::custom-fields'}
---

# Reorder custom fields

## Trigger

The order of fields matters.

## Outcome

Forms and PDFs show the fields in the new order.
