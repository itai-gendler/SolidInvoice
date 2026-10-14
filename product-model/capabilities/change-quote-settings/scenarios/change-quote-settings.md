---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the number format, email subject, BCC recipient or watermark used for quotations and saves
  kind: actor
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::settings'}
- text: The Product saves the company's quote settings
  kind: product
  actor: user
  entities:
  - {entity: company, effect: changes, facts: [Quote number format, Quote email subject, Quote BCC address, Quote watermark]}
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::settings'}
---

# Change quote settings

## Trigger

The company adjusts how it quotes.

## Outcome

New quotes and quote emails follow the new settings.
