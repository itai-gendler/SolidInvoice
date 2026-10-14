---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses what it applies to and enters the label, type, options, whether it is required, its visibility and default value, and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::custom-field-form'}
- text: The Product adds the field at the end of the list
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: creates, facts: [Applies to, Label, Type, Options, Required, Visibility, Default value, Position]}
  contexts:
    web: {place: 'web::company-workspace::custom-field-form'}
---

# Add a custom field

## Trigger

The company needs to record something extra.

## Outcome

The field appears on the matching forms, and client-visible invoice and quote fields on their PDFs.
