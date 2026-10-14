---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a tax identifier in the company section of the settings and chooses Save tax identifiers
  kind: actor
  actor: user
  entities:
  - {entity: tax-identifier, effect: reads, facts: [Type, Number, Primary]}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::settings'}
- text: The Product saves the tax identifier
  kind: product
  actor: user
  entities:
  - {entity: tax-identifier, effect: changes, facts: [Type, Number, Primary]}
  contexts:
    web: {place: 'web::company-workspace::settings'}
---

# Edit a company tax identifier

## Trigger

A registration number changes.

## Outcome

Documents prepared from now on show the new number.
