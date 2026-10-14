---
kind: alternative
routes:
  web: Web
steps:
- text: The User's integration sends a request to change a quote or add, change or remove its lines
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: rest-api}
- text: The Product saves the quote and recalculates its totals
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, facts: [Line items, Discount, Withholding and adjustments, Terms, Notes, Total, Tax total]}
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

# Edit a quote through the API

## Trigger

An integration acting for a User does this through the REST API.

## Outcome

The quote carries the new content.
