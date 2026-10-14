---
kind: alternative
routes:
  web: Web
steps:
- text: The User chooses Send on a pending quote
  kind: actor
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
- text: The Product emails the quote again to the contacts chosen on it
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  - {entity: contact, effect: reads, facts: [Email]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Send a pending quote again

## Trigger

The client asks for the quote again.

## Outcome

The contacts have the quote again; its status is unchanged.
