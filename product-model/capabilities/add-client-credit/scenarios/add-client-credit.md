---
kind: primary
routes:
  web: Web
steps:
- text: The User enters an amount in the client's currency and saves
  kind: actor
  actor: user
  entities:
  - {entity: client, effect: reads, facts: [Currency, Credit balance]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
- text: The Product adds the amount to the client's credit balance
  kind: product
  actor: user
  entities:
  - {entity: client, effect: changes, facts: [Credit balance]}
  contexts:
    web: {place: 'web::company-workspace::client-detail'}
---

# Add credit to a client

## Trigger

The client paid in advance, for example a retainer or deposit.

## Outcome

The client's credit balance is higher by the amount and can pay its invoices.
