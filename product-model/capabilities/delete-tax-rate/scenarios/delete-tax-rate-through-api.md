---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete a tax rate
  kind: actor
  actor: user
  entities:
  - {entity: tax-rate, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product deletes the tax rate
  kind: product
  actor: user
  entities:
  - {entity: tax-rate, effect: removes}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/Tax.php
---

# Delete a tax rate through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The rate is no longer offered.
