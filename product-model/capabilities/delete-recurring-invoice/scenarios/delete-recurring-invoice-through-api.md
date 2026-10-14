---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to delete a draft recurring invoice
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product deletes the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: removes, from: Draft}
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

# Delete a recurring invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The recurring invoice is gone.
