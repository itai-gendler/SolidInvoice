---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Archive on an accepted quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product archives the quote and lists it under Archived
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Accepted, to: Archived, facts: [Listed in Archived]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product returns to the quote list
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
---

# Archive a quote from its page

## Trigger

A quote is finished with.

## Outcome

The quote is Archived and listed under the Archived tab; no further changes are offered on it.

## Edge cases

- Quotes in any status except Archived can be archived from their page.
