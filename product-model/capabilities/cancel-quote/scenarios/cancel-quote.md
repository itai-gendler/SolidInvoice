---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Cancel on a pending quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product cancels the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Cancelled, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Cancel a pending quote

## Trigger

The company withdraws the offer.

## Outcome

The quote is Cancelled; it can be reopened.

## Edge cases

- A draft quote can be cancelled the same way.
