---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to create a quote for a client, with its lines and recipients
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product creates the quote as a Draft with the next quote number
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: creates, to: Draft, facts: [Quote number, Line items, Discount, Withholding and adjustments, Terms, Notes, Custom field values, Total, Tax total, Currency]}
  contexts:
    web: {place: rest-api}
references:
- kind: code
  role: implementation
  target: src/QuoteBundle/Entity/Quote.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/QuoteTransitionProcessor.php
- kind: code
  role: implementation
  target: src/ApiBundle/State/Processor/QuoteLinePersistProcessor.php
---

# Create a quote through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

A Draft quote exists for the client.
