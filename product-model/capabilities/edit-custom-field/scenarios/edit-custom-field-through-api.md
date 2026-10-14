---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to change a custom field
  kind: actor
  actor: user
  entities:
  - {entity: custom-field, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the field
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: changes, facts: [Label, Options, Required, Visibility, Default value]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/CustomField/CustomField.php
---

# Edit a custom field through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The field uses the new definition.
