---
kind: alternative
routes:
  web: Web
steps:
- text: The User selects one or more quotes and chooses Archive
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
- text: The Product lists the selected quotes under Archived, keeping their status
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: changes, facts: [Listed in Archived]}
  contexts:
    web: {place: 'web::company-workspace::quote-list'}
---

# Archive quotes from the quote list

## Trigger

The User tidies the active list.

## Outcome

The quotes are listed under Archived with their status unchanged.
