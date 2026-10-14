---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to read an invoice
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product returns the invoice with its lines, totals and balance
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Line items, Notes, Total, Balance, Due date]}
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

# Read an invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The integration has the invoice.
