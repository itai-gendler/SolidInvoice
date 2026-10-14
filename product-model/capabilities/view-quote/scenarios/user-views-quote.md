---
kind: alternative
routes:
  web: Web
steps:
- text: The User opens a quote from the quote list
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
- text: The Product shows the quote with its internal notes and the abilities its status allows
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number, Line items, Notes, Total]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# A user opens a quote

## Trigger

The User checks a quote.

## Outcome

The User sees the quote, including the notes the client never sees.
