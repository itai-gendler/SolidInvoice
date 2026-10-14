---
kind: primary
routes:
  web: Web
steps:
- text: The User selects one or more quotes that were archived from the list and chooses Activate
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
- text: The Product lists the selected quotes among the active quotes again
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, facts: [Listed in Archived]}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
---

# Activate archived quotes

## Trigger

An archived quote is needed again.

## Outcome

The quotes are back in the active list; their status is unchanged.
