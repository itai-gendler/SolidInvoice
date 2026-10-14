---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to send a draft quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product issues the quote and emails it to the contacts chosen on it
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Draft, to: Pending, facts: []}
  - {entity: contact, effect: reads, facts: [Email]}
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

# Send a quote through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The quote is Pending and its contacts have it by email.
