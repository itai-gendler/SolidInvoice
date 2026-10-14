---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the label, options, whether it is required, its visibility or default value, and saves
  kind: actor
  actor: user
  entities:
  - {entity: custom-field, effect: reads, facts: [Label, Type]}
  contexts:
    web: {place: 'web::company-workspace::custom-field-form'}
- text: The Product saves the field
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: changes, facts: [Label, Options, Required, Visibility, Default value]}
  contexts:
    web: {place: 'web::company-workspace::custom-field-form'}
---

# Edit a custom field

## Trigger

A field needs adjusting.

## Outcome

Forms and PDFs use the new definition.
