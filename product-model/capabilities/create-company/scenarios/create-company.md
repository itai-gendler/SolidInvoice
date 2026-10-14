---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the company name and currency and chooses Create Company
  kind: actor
  actor: user
  entities:
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::company-form'}
- text: The Product creates the company with the User in it and makes it the active company
  kind: product
  actor: user
  entities:
  - {entity: company, effect: creates, facts: [Name, Currency]}
  - {entity: user, effect: changes, facts: [Companies]}
  contexts:
    web: {place: 'web::company-workspace::company-form'}
- text: The Product opens the new company's dashboard
  kind: product
  actor: user
  entities:
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::dashboard'}
---

# Create a company

## Trigger

The User runs another business.

## Outcome

The new company is active, empty, and kept apart from the User's other companies.

## Edge cases

- A User who belongs to no company is taken to this form after signing in.
