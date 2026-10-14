---
kind: primary
routes:
  web: Web
steps:
- text: The User selects a draft quote and chooses Delete
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
- text: The Product deletes the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: removes, from: Draft}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
---

# Delete quotes from the quote list

## Trigger

A quote was created by mistake.

## Outcome

The quote is gone.

## Edge cases

- Quotes in any status can be deleted from the list.
