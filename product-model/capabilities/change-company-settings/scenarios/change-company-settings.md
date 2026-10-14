---
kind: primary
routes:
  web: Web
steps:
- text: The User changes the name, currency, logo or postal and contact details in the company section and saves
  kind: actor
  actor: user
  entities:
  - {entity: company, effect: reads, facts: [Name, Currency]}
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::settings'}
- text: The Product saves the company's details
  kind: product
  actor: user
  entities:
  - {entity: company, effect: changes, facts: [Name, Currency, Logo, Address, Email address, Phone number]}
  contexts:
    web: {place: 'web::company-workspace::settings'}
---

# Change company settings

## Trigger

The business's details change.

## Outcome

Documents prepared from now on show the new details; clients without their own currency follow the new currency.
