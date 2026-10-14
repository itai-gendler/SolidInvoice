---
kind: alternative
routes:
  web: Web
steps:
- text: The User enters a negative amount and saves
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Credit balance]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product subtracts the amount from the client's credit balance
  kind: product
  actor: user
  entities:
  - {entity: client, effect: changes, facts: [Credit balance]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Deduct credit from a client

## Trigger

Credit held for the client must be reduced.

## Outcome

The client's credit balance is lower by the amount, below zero if the deduction is larger than the balance.
