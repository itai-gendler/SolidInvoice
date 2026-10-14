---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to read a quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product returns the quote with its lines and totals
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number, Line items, Notes, Total, Tax total]}
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

# Read a quote through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The integration has the quote.
