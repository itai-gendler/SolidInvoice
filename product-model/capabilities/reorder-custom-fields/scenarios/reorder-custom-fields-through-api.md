---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to reorder the custom fields
  kind: actor
  actor: user
  entities:
  - {entity: custom-field, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the new positions
  kind: product
  actor: user
  entities:
  - {entity: custom-field, effect: changes, facts: [Position]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/CoreBundle/Action/Api/CustomFieldReorderAction.php
---

# Reorder custom fields through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The fields are in the new order.
