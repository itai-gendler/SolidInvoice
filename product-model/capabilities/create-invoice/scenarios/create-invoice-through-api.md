---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to create an invoice for a client, with its lines and recipients
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product creates the invoice as a Draft with the next invoice number
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/Invoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/InvoiceTransitionProcessor.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/InvoiceLinePersistProcessor.php
---

# Create an invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

A Draft invoice exists for the client.
