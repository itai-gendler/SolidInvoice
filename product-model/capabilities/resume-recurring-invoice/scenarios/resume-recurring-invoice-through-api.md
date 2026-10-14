---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to resume a paused recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product makes the recurring invoice active again
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, from: Paused, to: Active, facts: []}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/RecurringInvoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecurringInvoiceTransitionProcessor.php
---

# Resume a recurring invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The recurring invoice is Active.
