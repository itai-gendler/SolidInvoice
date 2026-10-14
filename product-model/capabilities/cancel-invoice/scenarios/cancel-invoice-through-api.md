---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to cancel a pending invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product cancels the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Pending, to: Cancelled, facts: []}
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

# Cancel an invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The invoice is Cancelled.
