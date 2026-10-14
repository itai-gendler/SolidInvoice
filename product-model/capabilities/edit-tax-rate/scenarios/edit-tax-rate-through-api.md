---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to change a tax rate
  kind: actor
  actor: user
  entities:
  - {entity: tax-rate, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the tax rate
  kind: product
  actor: user
  entities:
  - {entity: tax-rate, effect: changes, facts: [Name, Rate, Type, Category, Compound]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/Tax.php
---

# Edit a tax rate through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

Line taxes chosen from now on use the new values.
