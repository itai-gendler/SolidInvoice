---
kind: alternative
routes:
  web: Web
steps:
- text: The User enters the company name and currency and skips the client and invoice steps
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::onboarding'}
- text: The Product creates the company with the User in it
  kind: product
  actor: user
  entities:
  - {entity: company, effect: creates, facts: [Name, Currency]}
  - {entity: user, effect: changes, facts: [Companies, Onboarding]}
  contexts:
    web: {place: 'web::company-workspace::onboarding'}
- text: The Product opens the dashboard
  kind: product
  actor: user
  entities: []
  contexts:
    web: {place: 'web::company-workspace::dashboard'}
---

# Set up only the company

## Trigger

A new User wants to explore first.

## Outcome

The company exists and the User is on its dashboard.
