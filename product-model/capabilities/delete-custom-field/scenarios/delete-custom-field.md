---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Delete on a field and confirms
  kind: actor
  actor: user
  entities:
  - {entity: custom-field, effect: reads, facts: [Label]}
  contexts:
    web: {place: 'web::company-workspace::custom-fields'}
- text: The Product removes the field and its values on every record
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::custom-fields'}
---

# Delete a custom field

## Trigger

A field is no longer used.

## Outcome

The field and all its stored values are gone for good.
