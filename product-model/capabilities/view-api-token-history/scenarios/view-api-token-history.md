---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses View History on a token
  kind: actor
  actor: user
  entities:
  - {entity: api-token, effect: reads, facts: [Name]}
  contexts:
    web: {place: 'web::company-workspace::api-tokens'}
- text: The Product shows the token's recent successful requests
  kind: product
  actor: user
  entities:
  - {entity: api-token, effect: reads, facts: [Request history, Usage count, Last used]}
  contexts:
    web: {place: 'web::company-workspace::api-tokens'}
---

# View a token's request history

## Trigger

The User checks how a token is used.

## Outcome

The User sees each request's date, method, endpoint, status, IP address and user agent.
