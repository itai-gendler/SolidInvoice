---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Send on a draft quote
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
- text: The Product emails the quote, with its PDF and a link to view it, to the contacts chosen on the quote
  kind: product
  actor: user
  entities:
  - {entity: quote, effect: reads, facts: [Quote number]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Quote email subject, Quote BCC address]}
  contexts:
    web: {place: 'web::company-workspace::quote-detail'}
---

# Send a draft quote

## Trigger

A draft quote is ready to go to the client.

## Outcome

The quote is Pending and the chosen contacts have it by email.
