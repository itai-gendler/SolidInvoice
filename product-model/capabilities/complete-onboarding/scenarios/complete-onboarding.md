---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the company name and currency
  kind: actor
  actor: user
  entities:
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::onboarding'}
- text: The User enters a first client's name and email
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::onboarding'}
- text: The User describes a first invoice line and its amount
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::onboarding'}
- text: The Product creates the company with the User in it, the client with a contact, and a draft invoice for one item
  kind: product
  actor: user
  entities:
  - {entity: company, effect: creates, facts: [Name, Currency]}
  - {entity: user, effect: changes, facts: [Companies, Onboarding]}
  - {entity: client, effect: creates, to: Active, facts: [Name, Currency, Credit balance], with: company}
  - {entity: contact, effect: creates, facts: [First name, Email], with: client}
  - {entity: invoice, effect: creates, to: Draft, facts: [Invoice number, Line items, Total, Balance], with: client}
  contexts:
    web: {place: 'web::company-workspace::onboarding'}
- text: The Product takes the User to the new invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
---

# Set up a company, a first client and a first invoice

## Trigger

A new User starts out.

## Outcome

The company, its first client and a Draft invoice exist, and the User is looking at the invoice.
