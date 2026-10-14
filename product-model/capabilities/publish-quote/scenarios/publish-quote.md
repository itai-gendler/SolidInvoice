---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Publish on a draft quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product issues the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Draft, to: Pending, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Publish a draft quote

## Trigger

A draft quote is ready.

## Outcome

The quote is Pending; its tax rates and currency are fixed.
