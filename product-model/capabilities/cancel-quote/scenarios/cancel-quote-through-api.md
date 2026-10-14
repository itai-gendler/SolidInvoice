---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to cancel a pending quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product cancels the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Cancelled, facts: []}
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

# Cancel a quote through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The quote is Cancelled.
