---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to create a recurring invoice with its lines and schedule
  kind: actor
  actor: user
  entities:
  - {entity: recurring-invoice, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product creates the recurring invoice as a Draft
  kind: product
  actor: user
  entities:
  - {entity: recurring-invoice, effect: creates, to: Draft, facts: [Start date, Recurring type, Repeat days, End recurrence, End date, End after occurrences, Payment terms, Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/InvoiceBundle/Entity/RecurringInvoice.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecurringInvoiceTransitionProcessor.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/RecurringInvoiceLinePersistProcessor.php
---

# Create a recurring invoice through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

A Draft recurring invoice exists.
