---
kind: alternative
routes:
  web: Web
steps:
- text: The User removes a tax identifier in the company section of the settings and chooses Save tax identifiers
  kind: actor
  actor: user
  entities:
  - {entity: tax-identifier, effect: reads, facts: [Type, Number]}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::settings'}
- text: The Product removes the tax identifier
  kind: product
  actor: user
  entities:
  - {entity: tax-identifier, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::settings'}
---

# Remove a company tax identifier

## Trigger

The business is no longer registered.

## Outcome

The number no longer appears on the company's documents.
