---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to create a custom field
  kind: actor
  actor: user
  entities:
  - {entity: custom-field, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product adds the field
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: creates, facts: [Applies to, Label, Type, Options, Required, Visibility, Default value, Position]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/CustomField/CustomField.php
---

# Add a custom field through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The field appears on the matching forms.
