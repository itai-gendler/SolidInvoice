---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reopen on a cancelled quote
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
  - {entity: quote, effect: changes, from: Cancelled, to: Draft, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Reopen a cancelled quote

## Trigger

A withdrawn offer is back on the table.

## Outcome

The quote is a Draft again and can be changed and issued.
