---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User enters the company, a first client and a first invoice line
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  - {entity: company, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::onboarding'}
  capability: complete-onboarding
- text: The Product creates the company, the client with its contact and a draft invoice
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
  capability: complete-onboarding
- text: The Product takes the User to the new invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: complete-onboarding
- text: The User chooses Publish and Send
  kind: actor
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: send-invoice
- text: The Product issues the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: changes, from: Draft, to: Pending, facts: []}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: send-invoice
- text: The Product emails the invoice, with its PDF and a link to view and pay it, to the contacts chosen on the invoice
  kind: product
  actor: user
  entities:
  - {entity: invoice, effect: reads, facts: [Invoice number, Total, Due date]}
  - {entity: contact, effect: reads, facts: [Email]}
  - {entity: company, effect: reads, facts: [Invoice email subject, Invoice BCC address]}
  contexts:
    web: {place: 'web::company-workspace::invoice-detail'}
  capability: send-invoice
---

# Set up the company, then send the first invoice

## Trigger

A new User finishes the guided setup.

## Outcome

The first client has the first invoice.
