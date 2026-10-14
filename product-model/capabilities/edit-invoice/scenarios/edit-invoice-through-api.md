---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to change an invoice or add, change or remove its lines
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the invoice and recalculates its totals and balance
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, facts: [Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total, Balance]}
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

# Edit an invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The invoice carries the new content.
