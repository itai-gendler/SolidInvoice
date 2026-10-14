---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the client name, website, currency, due terms and extra field values, and any tax identifiers and addresses
  kind: actor
  actor: user
  entities:
  - {entity: tax-identifier, effect: reads, facts: []}
  - {entity: address, effect: reads, facts: []}
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The User adds at least one contact with a first name and email
  kind: actor
  actor: user
  entities:
  - {entity: contact, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The User saves the client
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The Product creates the active client with a zero credit balance, with its contacts, tax identifiers and addresses
  kind: product
  actor: user
  entities:
  - {entity: client, effect: creates, to: Active, facts: [Name, Website, Currency, Payment terms, Credit balance, Custom field values]}
  - {entity: contact, effect: creates, facts: [First name, Last name, Email, Additional contact details, Custom field values], with: client}
  - {entity: tax-identifier, effect: creates, facts: [Type, Number, Primary], with: client}
  - {entity: address, effect: creates, facts: [Street, City, State, Zip, Country], with: client}
  contexts:
    web: {place: 'web::company-workspace::client-form'}
- text: The Product shows the new client
  kind: product
  actor: user
  entities:
  - {entity: client, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Create a client with its contacts

## Trigger

The User wants to start billing someone new.

## Outcome

The client exists as Active with its contacts and can be chosen for quotes, invoices and recurring invoices.

## Edge cases

- Without a currency of its own the client follows the company currency.
