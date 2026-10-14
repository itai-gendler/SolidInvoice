---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a client from the client list
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::client-list'}
- text: The Product shows the client with its contacts, addresses, credit balance, totals invoiced and outstanding, and its quotes, invoices and payments
  kind: product
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Name, Website, Currency, Credit balance]}
  - {entity: contact, effect: reads, facts: [First name, Email]}
  - {entity: address, effect: reads, facts: [Street, City]}
  - {entity: invoice, effect: reads, facts: [Balance, Total]}
  - {entity: payment, effect: reads, facts: []}
  - {entity: quote, effect: reads, facts: []}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Open a client

## Trigger

The User looks a client up.

## Outcome

The User sees everything about the client in one place.
