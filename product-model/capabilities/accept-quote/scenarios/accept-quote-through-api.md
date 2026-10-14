---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to accept a pending quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product marks the quote accepted and creates a draft invoice from it
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Accepted, facts: []}
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Invoice date, Payment terms, Due date, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Balance, Currency]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Entity/Quote.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/QuoteTransitionProcessor.php
---

# Accept a quote through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The quote is Accepted and its invoice is a Draft.
