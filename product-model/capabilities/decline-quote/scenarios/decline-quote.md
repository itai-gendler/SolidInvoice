---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Decline on a pending quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product marks the quote declined
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, from: Pending, to: Declined, facts: []}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Decline a pending quote

## Trigger

The client says no.

## Outcome

The quote is Declined; it can be reopened.
