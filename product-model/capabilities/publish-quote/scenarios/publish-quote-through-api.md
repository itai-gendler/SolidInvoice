---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to publish a draft quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product issues the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Draft, to: Pending, facts: []}
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

# Publish a quote through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The quote is Pending.
