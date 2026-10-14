---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Reopen on a declined quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product returns the quote to draft
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Declined, to: Draft, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Reopen a declined quote

## Trigger

The client reconsiders.

## Outcome

The quote is a Draft again.
