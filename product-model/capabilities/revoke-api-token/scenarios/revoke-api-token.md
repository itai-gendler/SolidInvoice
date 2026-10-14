---
kind: primary
routes:
  web: Web
steps:
- text: The User selects one or more tokens and chooses Revoke
  kind: actor
  actor: user
  entities:
  - {entity: api-token, effect: reads, facts: [Name, Last used]}
  contexts:
    web: {place: 'web::company-workspace::api-tokens'}
- text: The Product deletes the tokens with their request history
  kind: product
  actor: user
  entities:
  - {entity: api-token, effect: removes}
  contexts:
    web: {place: 'web::company-workspace::api-tokens'}
---

# Revoke API tokens

## Trigger

An integration is retired or a token leaked.

## Outcome

Requests with the tokens are refused from now on.
