---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete a custom field
  kind: actor
  actor: user
  entities:
  - {entity: custom-field, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product removes the field and its values
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: removes}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Entity/CustomField/CustomField.php
---

# Delete a custom field through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The field is gone.
