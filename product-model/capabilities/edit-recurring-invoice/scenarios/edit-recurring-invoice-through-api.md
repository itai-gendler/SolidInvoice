---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to change a recurring invoice or its lines
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the recurring invoice
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: changes, facts: [Start date, Recurring type, Repeat days, End recurrence, End date, End after occurrences, Payment terms, Line items, Discount, Terms, Notes, Total, Tax total]}
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

# Edit a recurring invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

Invoices generated from now on use the new template.
