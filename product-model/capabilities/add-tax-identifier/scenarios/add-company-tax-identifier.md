---
kind: alternative
routes:
  web: Web
steps:
- text: The User adds a tax identifier in the company section of the settings and chooses Save tax identifiers
  kind: actor
  actor: user
  entities:
  - {entity: tax-identifier, effect: reads, facts: []}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::settings'}
- text: The Product adds the tax identifier to the company
  kind: product
  actor: user
  entities:
  - {entity: tax-identifier, effect: creates, facts: [Type, Number, Primary]}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::settings'}
references:
- kind: code
  role: implementation
  target: src/TaxBundle/Twig/Components/CompanyTaxIdentifiers.php
---

# Add a tax identifier to the company

## Trigger

The business is registered for a tax.

## Outcome

The number appears on every quote and invoice the company issues.
