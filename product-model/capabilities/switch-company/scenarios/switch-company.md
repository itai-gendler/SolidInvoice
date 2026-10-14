---
kind: primary
routes:
  web: Web
steps:
- text: The User picks another of their companies
  kind: actor
  actor: user
  entities:
  - {entity: company, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::company-picker'}
- text: The Product makes it the active company and opens its dashboard
  kind: product
  actor: user
  entities:
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::dashboard'}
---

# Switch to another company

## Trigger

The User wants to work on another business.

## Outcome

Everything the User sees and does now belongs to the chosen company.

## Edge cases

- After signing in, a User with one company goes straight to it; with several, they choose here.
