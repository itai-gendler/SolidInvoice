---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete a draft invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product deletes the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: removes, from: Draft}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/Invoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/InvoiceTransitionProcessor.php
---

# Delete an invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The invoice is gone.
