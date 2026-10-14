---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to add a tax identifier
  kind: actor
  actor: user
  entities:
  - {entity: tax-identifier, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product adds the tax identifier
  kind: product
  actor: user
  entities:
  - {entity: tax-identifier, effect: creates, facts: [Type, Number, Primary]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Entity/TaxIdentifier.php
- kind: code
  role: implementation
  target: src/TaxBundle/Form/Type/TaxIdentifierType.php
---

# Add a tax identifier through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The number is recorded.
